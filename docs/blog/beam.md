``` py title="data_pipeline.py"
import argparse
import logging
import json
import time
import traceback
from typing import Optional, List
import apache_beam as beam
from apache_beam import Create, Map, ParDo, Flatten, Keys
from apache_beam import Values, GroupByKey, CoGroupByKey, CombineGlobally, CombinePerKey
from apache_beam import pvalue, window, WindowInto
from apache_beam.transforms.util import WithKeys
from apache_beam.transforms.combiners import Top, Mean
from apache_beam.options.pipeline_options import PipelineOptions
from apache_beam.options import pipeline_options
from apache_beam.io.gcp.bigquery import BigQueryDisposition, WriteToBigQuery
from apache_beam.io.textio import , ReadFromText, WriteToText

def run(beam_args: Optional[List[str]] = None):
    pipeline_options = PipelineOptions(beam_args)
    with beam.Pipeline(options=pipeline_options, runner="DataflowRunner") as p:
    # File paths relative to the bucket

        data = (p | "Create file path tuple" >> ReadFromText("gs://bucket/test_file")
                  | "JSON MAP">> beam.Map(json.loads))

        bq = data | "WriteToBigQuery" >> WriteToBigQuery(table="project:beam_basics.test1", schema="SCHEMA_AUTODETECT",
                                                            create_disposition=BigQueryDisposition.CREATE_IF_NEEDED,
                                                            write_disposition=BigQueryDisposition.WRITE_APPEND)

        gcs = data | "WriteToGCS" >> WriteToText(file_path_prefix="gs://bucket/output/test_file_out", )

if __name__ == '__main__':
  logging.getLogger().setLevel(logging.INFO)
  
  parser = argparse.ArgumentParser()
  #parser.add_argument('--input', default = '')
  #parser.add_argument('--output', required =True)
  known_args, pipeline_args = parser.parse_known_args()
  
  run(pipeline_args)
```
# Week 2 - Observability 

## Distributed Tracing

### Create a new enviroment in Honeycomb and get the API Key
### Exporting API KEY

```
export HONEYCOMB_API_KEY="1MoygvY1GhDHYNGLJxjvUD"
gp env HONEYCOMB_API_KEY="1MoygvY1GhDHYNGLJxjvUD"

export HONEYCOMB_SERVICE_NAME="Cruddur"
gp env HONEYCOMB_SERVICE_NAME="Cruddur"
```
OTEL = Open Telemetry
We had a specific OTEL SERVICE in docker compose for the backend


INSTALL PACKAGES FOR PYTHON
[PACKAGES FOR PYTHON](https://ui.honeycomb.io/fjgh75922-gettingstarted/environments/bootcamp/send-data#)

```
pip install opentelemetry-api \
    opentelemetry-sdk \
    opentelemetry-exporter-otlp-proto-http \
    opentelemetry-instrumentation-flask \
    opentelemetry-instrumentation-requests
```

Added to requirements.txt

then run inside backend-flask

```
pip install -r requirements.txt
````

Added initialize instructions to app.py

```
from opentelemetry import trace
from opentelemetry.instrumentation.flask import FlaskInstrumentor
from opentelemetry.instrumentation.requests import RequestsInstrumentor
from opentelemetry.exporter.otlp.proto.http.trace_exporter import OTLPSpanExporter
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.trace.export import BatchSpanProcessor


provider = TracerProvider()
processor = BatchSpanProcessor(OTLPSpanExporter())
provider.add_span_processor(processor)
trace.set_tracer_provider(provider)
tracer = trace.get_tracer(__name__)
```
## Open docker ports automatically (Added on gitpod.yml)

´´´
ports:
  - name: frontend
    port: 3000
    onOpen: open-browser
    visibility: public
  - name: backend
    port: 4567
    visibility: public
  - name: xray-daemon
    port: 2000
    visibility: public
´´´

# Added Simple processor on app.py
# This is a Dockerfile useful for training models with Coqui STT in Jupyter notebooks

FROM ghcr.io/coqui-ai/stt-train:latest

#RUN cp -r /code/notebooks/* /workspace
RUN chown -R 42420:42420 /code/notebooks
WORKDIR /code/notebooks

RUN python3 -m pip install --no-cache-dir jupyter jupyter_http_over_ws
RUN jupyter serverextension enable --py jupyter_http_over_ws

EXPOSE 8080 
CMD ["bash", "-c", "jupyter lab --ip=0.0.0.0 --port=8080 --no-browser --allow-root \
  --LabApp.token='' \
  --LabApp.custom_display_url=${JOB_URL_SCHEME}${JOB_ID}.${JOB_HOST} \
  --LabApp.allow_remote_access=True \
  --LabApp.allow_origin='*' \
  --LabApp.disable_check_xsrf=True"]

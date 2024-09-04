FROM python:3.9-slim

LABEL author="Devops <devops@sirpi.io>"

ENV USER=app

RUN useradd -m ${USER}

USER app  

WORKDIR /home/${USER}

COPY --chown=${USER} requirements.txt .

ENV PATH="/home/${USER}/.local/bin:$PATH"

RUN pip install --no-cache-dir --upgrade -r requirements.txt

COPY --chown=${USER} Experiment1.py .

EXPOSE 8080

CMD [ "uvicorn", "Experiment1:app", "--host", "0.0.0.0", "--port", "8080" ]

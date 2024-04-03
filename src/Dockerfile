# syntax=docker/dockerfile:1
FROM python:3-alpine
ENV PYTHONUNBUFFERED=1
WORKDIR /usr/src/app
# Clone the repository from GitHub                         
RUN apt-get update && \                                    
RUN apt-get install -y git && \                            
RUN git clone https://github.com/FlowiseAI/Flowise.git . 
    
RUN npm install
COPY . .

COPY ./Flowise-main/docker/.env.example .env

COPY requirements.txt /usr/src/app/
RUN pip install -U -r requirements.txt
COPY ./web /usr/src/app/
COPY ./entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]

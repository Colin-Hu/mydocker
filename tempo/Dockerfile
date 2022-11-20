FROM python:3

RUN pip install pynacl discord asyncio youtube_search youtube_dl python-dotenv
RUN apt update
RUN apt-get -y install ffmpeg

CMD cd Tempo && \
    python bot.py

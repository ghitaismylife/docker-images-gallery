FROM python:3.9

WORKDIR /app

EXPOSE 5050

# Copy the Pipfiles (Pipfile and Pipfile.lock) into the container
COPY Pipfile Pipfile.lock ./

# Install Pipenv
RUN pip install pipenv

# Install project dependencies using Pipenv
RUN pipenv install --system --deploy --ignore-pipfile
# Create .env.local file and add UNSPLASH_KEY
RUN echo "UNSPLASH_KEY=eZUL-1YntFNO_iwfLTIsUMFG-fOCCFMwcLZhWE-mcv8" > .env.local
# Run pipenv lock and redirect output to requirements.txt
RUN /bin/bash -c "pipenv lock --requirements > requirements.txt || exit 0"
RUN pip install -r requirements.txt
# Copy your application code into the container
COPY . ./

CMD ["python", "main.py"]
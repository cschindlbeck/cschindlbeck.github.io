# Use a lightweight Ruby base image
FROM ruby:3.2-slim

# Set a working directory
WORKDIR /website

# Install required build tools and cleanup
RUN apt-get update && apt-get install -y --no-install-recommends \
  build-essential \
  zlib1g-dev \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install the specific Bundler version
RUN gem install bundler:2.6.2

# Copy application files
COPY . .

# Install application dependencies
RUN bundle install  
# --deployment --without development test

RUN bundle

# Set the default command to serve the site
# CMD ["bundle", "exec", "jekyll", "serve"]

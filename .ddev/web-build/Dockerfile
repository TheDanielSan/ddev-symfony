
#ddev-generated
# You can copy this Dockerfile.example to Dockerfile to add configuration
# or packages or anything else to your webimage
# These additions will be appended last to ddev's own Dockerfile

# install PHP AMQP extension in ddev environment
RUN if ! [ "$(php -m | grep 'amqp')" ]; then \
        apt update && DEBIAN_FRONTEND=noninteractive apt install --yes -o Dpkg::Options::="--force-confnew" --no-install-recommends --no-install-suggests php${DDEV_PHP_VERSION}-amqp; \
    else \
        echo "amqp for PHP already installed"; \
    fi

# Install symfony console in ddev environment
RUN if ! [ "$(dpkg -s symfony-cli | grep 'ok installed')" ]; then \
        # curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash; \
        curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | bash; \
        apt install --yes symfony-cli; \
    else \
        echo "symfony-cli is already installed"; \
    fi

RUN echo "Built on $(date)" > /var/www/html/build-date.txt

include util.mk


# =============
# Configuration
# =============

$(eval crossbar     := $(venv)/bin/crossbar)
$(eval pki-client   := $(venv)/bin/pki-client)


# =====
# Setup
# =====

# Install requirements for development.
setup-package: setup-virtualenv
	@test -e $(crossbar) || $(pip) install --requirement requirements.txt --upgrade


# ====
# Init
# ====
init: setup-package
	$(pki-client) \
        --ca-url=http://127.0.0.1:8000/ --ca-name=RootCA \
        --cacert=cacert.pem --key=crossbar.key --certificate=crossbar.pem --common-name-prefix=broker


# ===
# Run
# ===
run:
	$(crossbar) start --config=crossbar.json

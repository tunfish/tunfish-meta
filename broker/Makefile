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
        --ca-url=$(TF_CA_URL) --ca-name=RootCA \
        --cacert=cacert.pem --key=crossbar.key --certificate=crossbar.pem --profile=server --common-name-prefix=broker


# ===
# Run
# ===
run:
	$(crossbar) start --config=crossbar.json

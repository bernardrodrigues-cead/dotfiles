# Makefile
#
# Frederico Sales | Bernard Rodriguez | Pedro Hote
# <frederico.sales@uab.ufjf.br> | <bernard.rodriguez@uab.ufjf.br> | <pedro.hote@uab.ufjf.br>
# 2022
#


#
## settings
#
.PHONY: all \
		help \
		run \
		clean \
		migrate \
		migrations \
		superuser \
		clear \
		install \
		update \
		shell \
		app \
		db \
		crypto \
		static \
		pgdump \
		ignore


#
## PATH's
#
ARG          := $1
PORT         := 8000
DB_USER      := 'frederico'
DATABASE     := 'fsales'
PROJECT      := 'fredericosales'
SRC          := src/
VENV_BIN_DIR := /Users/frederico/.venvs/${PROJECT}/bin
ACTIVATE     := ${VENV_BIN_DIR}/activate
PYTHON_BIN   := ${VENV_BIN_DIR}/python
PIP_BIN      := ${VENV_BIN_DIR}/pip
MANAGE       := ${SRC}/manage.py
REQUIREMENTS := requirements/requirements.txt
DUMP         := scripts/${PROJECT}-`date +"%Y-%m-%d_%H-%M-%S"`.json
DATE         := `date +"%Y-%m-%d_%H-%M-%S"`


#
## targets
#


#: Do nothing.
all:
	@clear
	@echo ""
	@echo "This target do nothing."
	@echo "Try make help."
	@echo ""


#: Display help and targets.
help:
	@clear
	@echo "Display this help, and targets."
	@echo ""
	@echo "--------------------------------------------------"
	@grep -B1 -E "^[a-zA-Z0-9_-]+\:([^\=]|$$)" Makefile \
     | grep -v -- -- \
     | sed 'N;s/\n/###/' \
     | sed -n 's/^#: \(.*\)###\(.*\):.*/\2###\1/p' \
     | column -t  -s '###'
	 @echo "--------------------------------------------------"
	@echo ""


#: Run django application on default port: 8000
run:
	${PYTHON_BIN} ${MANAGE} runserver 0.0.0.0:${PORT}


#: Light cleaning.
clean:
	@clear
	@find . -name "*.pyc" -exec rm -f {} +
	@find . -type d -name "__pycache__" -exec rm -rf {} +
	@find . -type d -name ".DS_Store" -exec rm -rf {} +


#: Heavy clening.
clear:
	@clear
	@find . -name "*.pyc" -exec rm -f {} +
	@find . -type d -name "__pycache__" -exec rm -rf {} +
	@find . -type d -name ".DS_Store" -exec rm -rf {} +
	@find . -name "[0][0]*.py" -exec rm -f {} +


#: Migration
migrations:
	${PYTHON_BIN} ${MANAGE} makemigrations ${ARG}


#: Migrate
migrate:
	${PYTHON_BIN} ${MANAGE} migrate


#: Update the project requirements.
update:
	${PIP_BIN} install -U pip setuptools wheel
	${PIP_BIN} install -U -r ${REQUIREMENTS}


#: Create the superuser.
superuser:
	${PYTHON_BIN} ${MANAGE} createsuperuser


#: Duh self explanatory...
install:
	${PIP_BIN} install -U pip setuptools wheel
	${PIP_BIN} install -r ${REQUIREMENTS}


#: Run the freaking shell.
shell:
	${PYTHON_BIN} ${MANAGE} shell


#: Create an application.
.ONESHELLL:
app:
	@mkdir ${SRC}/${ARG}
	${PYTHON_BIN} ${MANAGE} startapp ${SRC}/${ARG}


#: Enter the SGDB matrix.
db:
	${PYTHON_BIN} ${MANAGE} dbshell


#: Dump the database to script folder.
dump:
	${PYTHON_BIN} ${MANAGE} dumpdata --indent=4 -a -o ${DUMP}


#: Generate the cryptographic key for encrypted fields.
crypto:
	${PYTHON_BIN} ${MANAGE} generate_encryption_key


#: Collect all static files and update in project.
static:
	${PYTHON_BIN} ${MANAGE} collectstatic


#: Dump the database to a file.
pgdump:
	@pg_dump -U ${DB_USER} -d ${DATABASE} -Z 9 -f scripts/${PROJECT}-${DATE}.sql.gz


#: Update gitignore files.
ignore:
	@git rm -r --cached .
	@git add .
	@git commit -m "Update gitignore: ${DATE}."

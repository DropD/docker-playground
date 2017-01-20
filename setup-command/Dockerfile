from ricoh/aiida

#~ run /etc/init.d/postgresql start
#~ USER postgres
#~ run /etc/init.d/postgresql start &&\
    #~ psql template1 -c "create user aiida with superuser password 'aiida';"
#~ USER root
workdir aiida_core
run git fetch
run git checkout issue_321
run pip install -e .
user postgres
run /etc/init.d/postgresql start &&\
    psql -c "CREATE USER root WITH SUPERUSER PASSWORD 'aiida';" &&\
    psql -c "CREATE DATABASE aiida_sqlalchemy OWNER root;" &&\
    psql -c "GRANT ALL PRIVILEGES ON DATABASE aiida_sqlalchemy TO root;"
user root
run /etc/init.d/postgresql start &&\
    verdi setup --non-interactive --backend='sqlalchemy' --email="aiida@localhost" --db_host="localhost" --db_port=5432 --db_name="aiida_sqlalchemy" --db_user=root --db_pass='aiida' --repo="/tmp/aiida_sqlalchemy/" --first-name=AiiDA --last-name=Verdi --institution="AiiDA Team" --no-password
cmd echo $(verdi profile list)

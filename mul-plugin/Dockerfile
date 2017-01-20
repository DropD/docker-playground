from aiida/plugins

run git pull
run echo $(pwd)
run pip install -e .
#~ user postgres
#~ run psql -c "CREATE USER root WITH SUPERUSER PASSWORD 'aiida';"
#~ run psql -c "CREATE DATABASE aiida OWNER root;"
#~ run psql -c "GRANT ALL PRIVILEGES ON DATABASE aiida TO root;"
#~ user root
cmd verdi quicksetup --first-name=AiiDA --last-name=Verdi --email=aiida@localhost --institution=AiiDA-Team --db-port=4321 #--db-user=root --db-user-pw='aiida'

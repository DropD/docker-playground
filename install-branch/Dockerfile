from aiida/buildenv

arg branch=develop
run pip install --upgrade pip setuptools
run git clone https://github.com/DropD/aiida_core.git
workdir aiida_core
run git fetch
run git checkout $branch
run pip install -Ue .[ssh,verdi_shell,REST] --process-dependency-links
run pip install -Ur optional_requirements.txt
run ssh-keygen -t rsa -N "" -f "${HOME}/.ssh/id_rsa"
run cp "${HOME}/.ssh/id_rsa.pub" "${HOME}/.ssh/authorized_keys"
run if [ ! -d "${HOME}/.ssh/" ]; then mkdir "${HOME}/.ssh/"; fi
run ssh-keyscan -H localhost >> "${HOME}/.ssh/known_hosts"
# entrypoint ['/etc/init.d/postgresql', 'start']

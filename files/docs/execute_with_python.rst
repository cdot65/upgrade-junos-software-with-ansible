========================
Prepare Your Environment
========================

This section should only be executed once. Refer to the other section regarding execution.

---------------------
With Poetry installed
---------------------

I have included a `poetry`_ file for anyone saavy enough to take advantage. For the uninitiated, Poetry helps replicate Python environments between users with a single file. You'll need to have Poetry installed on your machine, for most users that will be solved with `pip install poetry`.

.. _poetry: https://python-poetry.org/docs/


.. code-block:: bash

    $ poetry install

.. image:: ../images/poetry_install.png
   :width: 600

---------------------------------------
Without Poetry installed on your system
---------------------------------------

Always, always, always strive to use virtual environments when working with Python. If you're needing a quick overview or refresher on Python virtual environments: 

[Digital Ocean (macOS)](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-macos)
[Digital Ocean (Windows 10)](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-windows-10)

.. code-block:: bash

    $ python3 -m venv venv
    $ source venv/bin/activate
    $ pip install -r files/docker/requirements.txt

.. image:: ../images/pip_install.png
   :width: 600

---------------------------------
Install Juniper's Ansible modules
---------------------------------

This is a one-time setup and should be skipped in additional playbook executions.

We will change into the directory containing our Ansible files, run our Ansible Galaxy install command to install the Ansible modules from Galaxy.

.. code-block:: bash
    $ cd files/ansible
    $ ansible-galaxy install juniper.junos --roles-path ./

.. image:: ../images/ansible_install.png
   :width: 600

================
Execute playbook
================

Execute the playbook, making sure to reference the inventory file for our environment in another directory.

.. code-block:: bash
    $ ansible-playbook pb.get.security_zones.yaml -i ../docker/inventory.yaml
===================
Execute with Docker
===================

---------------------
With Invoke installed
---------------------

If you have `invoke`_ installed, you can use these two commands to build the container and run the playbook.

.. _invoke: https://pypi.org/project/invoke/


.. code-block:: bash

    $ invoke build
    $ invoke shell


Build the container image

.. image:: ../images/docker_build.png
   :width: 600

Execute the container

This playbook is expected to be ran in Ansible AWX, so many of the elements in the playbook are stored as variables. We will need to pass in values for these objects when we run our playbook


.. code-block:: bash

    $ ansible-playbook pb.junos.upgrade.yaml -i inventory.yaml -e device_name=Richmond-fw1 -e software_version='junos-srxsme-20.4R1.12.tgz'


.. image:: ../images/ansible_install.png
   :width: 600

---------------------------------------
Without Invoke installed on your system
---------------------------------------

.. code-block:: bash

    $ docker build -t registry.gitlab.com/cremsburg/juniper-automation-container:software-upgrade files/docker/
    $ docker run -it \
        --rm \
        --env-file $(pwd)/files/docker/.env \
        -v $(pwd)/files/ansible/:/home/ansible \
        -w /home/ansible/ \
        registry.gitlab.com/cremsburg/juniper-automation-container:software-upgrade ansible-playbook pb.junos.upgrade.yaml \
        -i inventory.yaml \
        -e device_name=Richmond-fw1 \
        -e software_version='junos-srxsme-20.4R1.12.tgz'


.. image:: ../images/docker_run.png
   :width: 600

------------------
Notes about Docker
------------------

If you are unsure if Docker is installed on your computer, then it's probably safe to suggest that it's not. If you're interested in learning more about the product, I encourage you to read a few blogs on the topic. A personal recommendation would be 

https://www.digitalocean.com/community/tutorial_collections/how-to-install-and-use-docker

Some of the goodies placed in the `docker` folder are not relevant to our use case with Python. Feel free to delete them as you see fit, I simply wanted to share with you my Docker build process for all Juniper automation projects (including those based on Ansible). The world is your oyster and I won't judge you on whatever direction you take.
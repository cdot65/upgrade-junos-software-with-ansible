=====================
pb.junos.upgrade.yaml
=====================

----------------
Upgrade software
----------------

We will be using Ansible to issue RPC calls to being a software download / install / reboot process on a device running Junos.

RETRIEVE NAT COUNTERS
=====================

In this first block we will issue the downloading / install of a remote image on the device. A reboot is also issued.

Authentication
--------------

There is an expectation that you pass your username/password combination. In the example above, we are executing the playbook through Ansible AWX/Tower, so authentication is taken care of for us.

The Docker execution will have an `.env` file for you to update with your username/password.

The native execution with Python will need to add the `user` and `passwd` as extra variables, or update the module accordingly, check out the [Docker](files/docs/execute_with_docker.rst) for an example

Example
-------

Here is the YAML defining our task from the playbook:

.. code-block:: yaml

      - name: Execute a basic Junos software upgrade.
        software:
          # fyi: upgrade_server is stored in group_vars/all.yaml
          remote_package: "http://{{ upgrade_server }}/images/{{ software_version }}"
          reboot: true
          validate: false
        register: response


Explanation
-----------

We leverage the Ansible module `software` from the juniper.device collection to issue our request.

There are many options for a remote_package, I encourage you to check out the official `documentation`_ to learn more about your options here.

.. _documentation: https://ansible-juniper-collection.readthedocs.io/en/latest/software.html

The `reboot: true` will reload the box, but you didn't need me to tell you that, right?

Finally, setting `validate: false` will prevent the box from undergoing the data model validation between your current and future OS.

The success and failure of our task is stored in an object called `response`, which will be used in our subsequent tasks.

=========
Inventory
=========

Our inventory is found at `files/ansible/inventory.yaml`, please update to reflect your own environment

.. code-block:: yaml

      ---
      all:
         children:
            firewalls:
               hosts:
                  Lafayette-fw1:
                     ansible_host: 192.168.105.136
                  Richmond-fw1:
                     ansible_host: 192.168.105.121

There is a top level group called `all`, which we will be calling in our playbook.

We create our own group called `firewalls`, and embed the hosts `Lafayette-fw1` and `Richmond-fw1` within it.

Each host has a unique IP address, so we declare that at the host level with `ansible_host` key.
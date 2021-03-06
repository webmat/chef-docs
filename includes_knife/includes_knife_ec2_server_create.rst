.. The contents of this file are included in multiple topics.
.. This file describes a command or a sub-command for Knife.
.. This file should not be changed in a way that hinders its ability to appear in multiple documentation sets.


The ``server create`` argument is used to create a new |amazon ec2| cloud instance. This will provision a new image in |amazon ec2|, perform a |chef| bootstrap (using the |ssh| protocol), and then install |chef| on the target system so that it can be run as a |chef client| and communicate with a |chef server|.

This argument has the following syntax::

   knife ec2 server create (options)

This argument has the following options:

``-A KEY``, ``--aws-access-key-id KEY``
   |aws-access-key-id|

``-bootstrap-protocol PROTOCOL``
   |bootstrap protocol|

``--bootstrap-version VERSION``
   |bootstrap-version|

``-d DISTRO``, ``--distro DISTRO``
   |distro|

``--ebs-size SIZE``
   |ebs-size|

``--ebs-no-delete-on-term``
   |ebs-no-delete-on-term|

``-ephemeral DEVICE``
   |ephemeral device|

``-f FLAVOR``, ``--flavor FLAVOR``
   |flavor|

``-fqdn FQDN``
   |fqdn amazon ec2|

``-g X,Y,Z``, ``--security-group-ids X,Y,Z``
   |group ids| Required when using |amazon vpc|.

``-G X,Y,Z``, ``--groups X,Y,Z``
   |groups| Not supported when using |amazon vpc|.

``-hint HINT_NAME[=HINT_FILE]``
   |hint|

``-i IDENTITY_FILE``, ``--identity-file IDENTITY_FILE``
   |identity-file|

``-I IMAGE``, ``--image IMAGE``
   |image|

``-K SECRET``, ``--aws-secret-access-key SECRET``
   |aws-secret-access-key|

``-N NAME``, ``--node-name NAME``
   |node-name|

``--[no-]host-key-verify``
   |[no-]host-key-verify|

``-p PORT``, ``--ssh-port PORT``
   |ssh-port|

``-P PASSWORD``, ``--ssh-password PASSWORD``
   |ssh-password|

``--prerelease``
   |prerelease|

``-r RUN_LIST``, ``--run-list RUN_LIST``
   |run-list|

``--region REGION``
   |region amazon|

``-s SUBNET_ID``, ``--subnet SUBNET_ID``
   |subnet|

``-S KEY``, ``--ssh-key KEY``
   |ssh-key amazon ec2|

``-server-connect-attribute ATTRIBUTE``
   |attribute ssh| This should be an |amazon ec2| server attribute.

``--T Tag=Value[,Tag=Value]``, ``--tags Tag=Value[,Tag=Value]``
   |tags|

``--template-file TEMPLATE``
   |template-file|

``-u USER_DATA_FILE``, ``--user-data USER_DATA_FILE``
   |user-data|

``-w GATEWAY``, ``--ssh-gateway GATEWAY``
   |ssh-gateway|

``-x USERNAME``, ``--ssh-user USERNAME``
   |ssh-user|

``-Z ZONE"``, ``--availability-zone ZONE``
   |availability-zone amazon ec2|

**Examples**

For example, to launch a new Amazon EC2 instance with the "webserver" role, enter:

.. code-block:: bash

   $ knife ec2 server create -r "role[webserver]" -I ami-2d4aa444 --flavor m1.small -G www,default -x ubuntu -N server01

To launch a new Amazon EC2 instance with multiple roles, enter:

.. code-block:: bash

   $ knife ec2 server create -r "role[base],role[webserver]" -I ami-2d4aa444 -G www,default -x ubuntu --node-name server01




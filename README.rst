kofa-vagrant
************

A vagrant_ machine running `kofa`_.


Initialize
==========

Clone this repo locally::

  $ git clone https://github.com/WAeUP/kofa-vagrant

Then fire up a local `vagrant`_ box::

  $ cd kofa-vagrant
  $ vagrant up

This will fetch a complete vagrant_ image (several hundreds MB) if you
do not have one stored locally already.

The machine will be provisioned using ansible_. This might take a
considerable amount of time.


Run Kofa
========

ssh into the vagrant box and start kofa:

  $ vagrant ssh
  vagrant@kofa:~ $ cd waeup.kofa-1.5
  vagrant@kofa:~/waeup.kofa-1.5 $ ./bin/kofactl start
  .
  daemon process started, pid=13363

You should now be able to browse kofa at port 8080 of your vagrant
box:

  http://192.168.33.33:8080

You should be asked for your credentials (``grok`` / ``grok`` by
default).

Then you can create and browse a `University` via the webinterface.


.. _ansible: https://docs.ansible.com/ansible/
.. _kofa: https://pypi.python.org/pypi/waeup.kofa
.. _vagrant: https://www.vagrantup.com/

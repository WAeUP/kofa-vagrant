kofa-vagrant
************

vagrant_ machines running `kofa`_.


Initialize
==========

Clone this repo locally::

  $ git clone https://github.com/WAeUP/kofa-vagrant

Then fire up local `vagrant`_ boxes::

  $ cd kofa-vagrant
  $ vagrant up

This will fetch complete vagrant_ images (several hundreds MB per box) if you
do not have stored them locally already.

The machines will be provisioned using ansible_ (and a little shell script
preparing the ground for ansible). This might take a considerable amount of
time.

Currently we provide two boxes, Ubuntu 14.04 ("trusty") and 16.04 ("xenial").
If you want to work with one of them only, specify the desired version in
your command:

  - ``trusty``
  - ``xenial``

For instance to initialize only the 14.04er box, run::

  $ vagrant up trusty

The same applies for all other vagrant_ commands described in here.


Run Kofa
========

ssh into the vagrant box and start kofa:

  $ vagrant ssh xenial  # or 'trusty'
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

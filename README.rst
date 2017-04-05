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

When run for the first time on a system, this will fetch complete vagrant_
images (several hundreds MB per box).

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


Install nginx as web proxy (optional)
=====================================

Kofa is normally run behind a webserver that acts as a proxy. We recommend
`nginx` for that. The local ``nginx.yml`` file is an ansible_ playbook to
create and configure an nginx server running inside your vagrant box.

Run it like this (not run by default)::

  $ ansible-playbook -u vagrant -k -i 192.168.33.33, nginx.yml

(mind the trailing comma behind the IP number). The default password of
`vagrant` is ``vagrant``.

Inside the vagrant machine you must start Zope/grok and then create and run a
Kofa instance (you need something to be proxied, right?). We first start Zope::

  $ vagrant ssh trusty       # or xenial
  (vagrant) $ cd waeup.kofa-1.5
  (vagrant) $ ./bin/kofactl start

Now we should be able to access the raw webinterface and create an Kofa
instance called `app`:

1) Open 192.168.33.33:8080 in your browser
2) Login (grok/grok)
3) Create a "University" instance called `app`.

If you pick another name, you must change the nginx config later accordingly.

If everthing went smooth, you should be able to browse to 192.168.33.33 at port
80 and even at port 443 as we create a self-signed SSL certificate when running
the playbook.

.. _ansible: https://docs.ansible.com/ansible/
.. _kofa: https://pypi.python.org/pypi/waeup.kofa
.. _vagrant: https://www.vagrantup.com/

============================
OpenFire (Instant Messaging)
============================

The OpenFire XMPP/Jabber server requires little attention from the Tuleap
administrators.

You may need to synchronize the OpenFire server with the Tuleap database in
some cases (e.g. the OpenFire server was down for some time). Symply go to the
Tuleap Administration page and select the "Instant Messaging" link.

The OpenFire administrative interface is available from the main Tuleap
administration page. By default, only the 'admin' user (same password as for
Tuleap) has access to the OpenFire administration interface, but other users
can be added easily.

The following chapter add more details about how you may proceed to configure
JabbeX. For further information on how to install and setup Openfire Jabber
server please refer to its `official website`_.

JabbeX Configuration
====================

.. NOTE::
  JabbeX is a middleware used by Tuleap Instant Messaging (IM) plug-in to
  communicate with the Jabber server. The Tuleap IM plug-in relies on
  JabbeX to perform any operation related to the Jabber server.


The JabbeX configuration parameters are all found in the
``jabbex_conf.xml`` file in the ``etc/`` directory of your JabbeX installation.
This file has the following structure:

.. code-block:: xml

        <?xml version="1.0" encoding="UTF-8"?>
        <!--Configuration file for JabbeX middleware-->
        <conf>
            <!--jabber server general parameters-->
            <server name="openfire">
                    <server_uri>tuleap.example.com</server_uri>
                    <server_port>5222</server_port>
            </server>

            <!--authentication credentials-->
            <auth>
                    <username>imadmin</username>
                    <user_pwd>usecret</user_pwd>
                    <lockmuc_pwd>mucsecret</lockmuc_pwd>
            </auth>

            <!--helga bot related information-->
            <helga>
                    <helga_bot>bot</helga_bot>
                    <helga_service>helga</helga_service>
            </helga>

            <!-- defines whether the shared group management feature is
            active or not. set this to 0 (false) only if using a jabber server
            other than openfire to which no compliant groupmanagerinterface is
            available. -->
            <group_mng>
                    <active>1</active>
            </group_mng>
        </conf>

Below we define what each of these parameters stands for.

* ``server``: information on the Jabber server bundled with Tuleap.  

* ``name``: stands for the server name and is used by JabbeX to define
  which file to use in several situations. Therefore, you will
  probably never need to change its value.  

* ``server_uri``: stands for the complete URI of your Jabber server or
  alternatively its IP address, so you need to set this value to the
  address of your Jabber server. 

* ``port``: defines which TCP port is used by your Jabber server. The
  default port for the Jabber protocol is 5222, we strongly
  recommend you not to change this value unless you have very strong
  reasons. 

* ``auth``: authentication credentials for the JabbeX Jabber user. This
  user must exist in the Tuleap environment and must be a member of the
  group defined by Openfire's property ``plugin.helga.group.admin``.

  .. NOTE::
    A list of all the properties defined in the Openfire
    environment is available through the web Administration Console of the
    server in the section “System Properties”.

* ``username``: must be the same username used in the Tuleap
  environment. 

* ``password``: must be the Tuleap password for this user. 

* ``lockmuc_pwd``: is a password used to lock MUC rooms when projects
  are in a state other than “Active”. Warning: This password is also
  used to unlock MUC rooms, so if you change it JabbeX will not be
  able to unlock any MUC room locked with the previous password, and
  you will must do it manually through the web Administration
  Console. 

* ``helga``: The Openfire Helga plug-in is used to allow further control over
  shared groups. Chances are that you will never need to change these values,
  but if you need to do it please refer to the `official plug-in
  documentation`_.

* ``helga_bot``: stands for the Helga bot username (“bot” by default) 

* ``helga_service``: stands for the name of the service the Helga
  plug-in creates when it is installed (“helga” by default). 

* ``group_mng``: The JabbeX shared group management feature is exclusive
  for Openfire, therefore the middleware allows you to deactivate it by
  setting the property active to 0 (false). Setting this value to 0
  will cause JabbeX not to perform any operation related to shared
  groups management. 

.. _`official website`: http://www.igniterealtime.org/projects/openfire/index.jsp
.. _`official plug-in documentation`: http://www.igniterealtime.org/community/docs/DOC-1080


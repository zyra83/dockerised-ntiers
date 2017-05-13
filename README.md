Reverse (nginx apache)
192.168.9.2 (443, 80)
frontal ->
  - /etc/hostname
  - /etc/hosts


AppServer
192.168.9.3 (4848, 8080)


export http_proxy=http://10.10.10.7:8080


Toutes les instances de glassfish sont lancées dans 
/opt/payara41/glassfish/domains/

/opt/payara41/glassfish/bin/asadmin start-domain domain1

**logs**
/opt/payara41/glassfish/domains/domain1/logs/server.log


Creating the connection pool - From the command line
 
You can also create a connection pool using the asadmin command line tool with the following (substituting your password for the test one) :
 
asadmin create-jdbc-connection-pool 
--datasourceclassname com.mysql.jdbc.jdbc2.optional.MysqlDataSource 
--restype javax.sql.DataSource
 --property user=root:password=test:DatabaseName=test:ServerName=localhost:port=3306 test-pool
 
To test the connection from the command line run the following command:
 
asadmin ping-connection-pool test-pool



NAME
       list-commands - lists available commands

SYNOPSIS
           list-commands [--help]
           [--localonly={false|true}] [--remoteonly={false|true}]

           pattern-list

DESCRIPTION
       The list-commands subcommand lists the asadmin subcommands.

       By default, the list-commands subcommand displays a list of local
       subcommands followed by a list of remote subcommands. You can specify
       that only remote subcommands or only local subcommands are listed and
       that only subcommands whose names contain a specified text string are
       listed.

       This subcommand is supported in local mode and remote mode.

OPTIONS
       --help, -?
           Displays the help text for the subcommand.

       --localonly
           If this option is set to true, only local commands are listed.
           Default is false.

           If this option is set to true, the --remoteonly option must be set
           to false. Otherwise, an error occurs.

       --remoteonly
           If this option is set to true, only remote commands are listed.
           Default is false.

           If this option is set to true, the --localonly option must be set
           to false. Otherwise, an error occurs.

OPERANDS
       pattern-list
           A space-separated list of text strings on which to filter the list
           of subcommands. Only the subcommands that contain any one of the
           specified text strings is listed.

EXAMPLES
       Example 1, Listing the Local Subcommands
           This example lists only the local subcommands.

               asadmin> list-commands --localonly=true
               ********** Local Commands **********
               change-admin-password
               change-master-password
               create-domain
               create-service
               delete-domain
               export
               help
               list-commands
               list-domains
               login
               monitor
               multimode
               restart-domain
               start-database
               start-domain
               stop-database
               stop-domain
               unset
               verify-domain-xml
               version
               Command list-commands executed successfully.

       Example 2, Filtering the Subcommands That Are Listed
           This example lists only the subcomands whose names contain the text
           configure or set.

               asadmin> list-commands configure set
               ********** Local Commands **********
               setup-ssh
               unset

               ********** Remote Commands **********
               configure-jms-cluster                   set-log-levels
               configure-lb-weight                     set-web-context-param
               configure-ldap-for-admin                set-web-env-entry
               set                                     unset-web-context-param
               set-log-attributes                      unset-web-env-entry

               Command list-commands executed successfully.

       Example 3, Listing All Subcommands
           This example first displays a list of the local subcommands,
           followed by a partial list of the remote subcommands.

               asadmin> list-commands
               ********** Local Commands **********
               change-admin-password
               change-master-password
               create-domain
               create-service
               delete-domain
               export
               help
               list-commands
               list-domains
               login
               monitor
               multimode
               restart-domain
               start-database
               start-domain
               stop-database
               stop-domain
               unset
               verify-domain-xml
               version
               ********** Remote Commands **********
               __locations                             enable
               add-resources                           enable-monitoring
               configure-ldap-for-admin                flush-jmsdest
               create-admin-object                     freeze-transaction-service
               create-audit-module                     generate-jvm-report
               create-auth-realm                       get
               create-connector-connection-pool        get-client-stubs
               create-connector-resource               get-host-and-port
               create-connector-security-map           jms-ping
               create-connector-work-security-map      list
               create-custom-resource                  list-admin-objects
               create-file-user                        list-app-refs
               create-http                             list-applications
               create-http-listener                    list-audit-modules
               create-iiop-listener                    list-auth-realms
               create-javamail-resource                list-components
               create-jdbc-connection-pool             list-connector-connection-pools
               create-jdbc-resource                    list-connector-resources
               create-jms-host                         list-connector-security-maps
               create-jms-resource                     list-connector-work-security-maps
               create-jmsdest                          list-containers
               create-jndi-resource                    list-custom-resources
               create-jvm-options                      list-file-groups
               create-lifecycle-module                 list-file-users
               create-message-security-provider        list-http-listeners
               create-network-listener                 list-iiop-listeners
               create-password-alias                   list-javamail-resources
               create-profiler                         list-jdbc-connection-pools
               create-protocol                         list-jdbc-resources
               create-resource-adapter-config          list-jms-hosts
               create-resource-ref                     list-jms-resources
               create-ssl                              list-jmsdest
               create-system-properties                list-jndi-entries
               create-threadpool                       list-jndi-resources
               create-transport                        list-jvm-options
               create-virtual-server                   list-lifecycle-modules
               delete-admin-object                     list-logger-levels
               delete-audit-module                     list-message-security-providers
               ...


               $PAYARA_PATH/bin/asadmin --user $ADMIN_USER --passwordfile=/opt/pwdfile list-jdbc-connection-pools



# LOGSPOUT

--build-arg http_proxy=http://user:motdepasse@monproxy.com:3128 --build-arg https_proxy=https://user:motdepasse@monproxy.com:3128


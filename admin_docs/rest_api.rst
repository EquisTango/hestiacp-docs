##################################
REST API
##################################

The Hestia WEB API is available to perform core functions of the Control Panel. We use it internaly to synchronyze DNS clusters, to integrate WHMC billing system and to reset mail account passwords in Roundcube. The API can be used as well to create new user accounts, domains, databases or even to build an alternative web interface.

This reference provides php code samples demonstrating how you can seamlessly integrate API into your application or script. However you can use other languages to commmunicate with API.


************************************************
Create User Account
************************************************

.. code-block:: php

    <?php

    // Server credentials
    $hst_hostname = 'server.hestiacp.com';
    $hst_username = 'admin';
    $hst_password = 'p4ssw0rd';
    $hst_returncode = 'yes';
    $hst_command = 'v-add-user';

    // New Account
    $username = 'demo';
    $password = 'd3m0p4ssw0rd';
    $email = 'demo@gmail.com';
    $package = 'default';
    $fist_name = 'Rust';
    $last_name = 'Cohle';

    // Prepare POST query
    $postvars = array(
        'user' => $hst_username,
        'password' => $hst_password,
        'returncode' => $hst_returncode,
        'cmd' => $hst_command,
        'arg1' => $username,
        'arg2' => $password,
        'arg3' => $email,
        'arg4' => $package,
        'arg5' => $fist_name,
        'arg6' => $last_name
    );
    $postdata = http_build_query($postvars);

    // Send POST query via cURL
    $postdata = http_build_query($postvars);
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, 'https://' . $hst_hostname . ': ' . $hst_port . '/api/');
    curl_setopt($curl, CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
    curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS, $postdata);
    $answer = curl_exec($curl);

    // Check result
    if($answer == 0) {
        echo "User account has been successfuly created\n";
    } else {
        echo "Query returned error code: " .$answer. "\n";
    }


************************************************
Add Web/DNS/Mail Domain
************************************************

.. code-block:: php

    <?php

    // Server credentials
    $hst_hostname = 'server.hestiacp.com';
    $hst_username = 'admin';
    $hst_password = 'p4ssw0rd';
    $hst_returncode = 'yes';
    $hst_command = 'v-add-domain';

    // New Account
    $username = 'demo';
    $domain = 'demo.hestiacp.com';

    // Prepare POST query
    $postvars = array(
        'user' => $hst_username,
        'password' => $hst_password,
        'returncode' => $hst_returncode,
        'cmd' => $hst_command,
        'arg1' => $username,
        'arg2' => $domain
    );
    $postdata = http_build_query($postvars);

    // Send POST query via cURL
    $postdata = http_build_query($postvars);
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, 'https://' . $hst_hostname . ': ' . $hst_port . '/api/');
    curl_setopt($curl, CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
    curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS, $postdata);
    $answer = curl_exec($curl);

    // Check result
    if($answer == 0) {
        echo "Domain has been successfuly created\n";
    } else {
        echo "Query returned error code: " .$answer. "\n";
    }


************************************************
Create Database
************************************************

.. code-block:: php

    <?php

    // Server credentials
    $hst_hostname = 'server.hestiacp.com';
    $hst_username = 'admin';
    $hst_password = 'p4ssw0rd';
    $hst_returncode = 'yes';
    $hst_command = 'v-add-database';

    // New Database
    $username = 'demo';
    $db_name = 'wordpress';
    $db_user = 'wordpress';
    $db_pass = 'wpbl0gp4s';

    // Prepare POST query
    $postvars = array(
        'user' => $hst_username,
        'password' => $hst_password,
        'returncode' => $hst_returncode,
        'cmd' => $hst_command,
        'arg1' => $username,
        'arg2' => $db_name,
        'arg3' => $db_user,
        'arg4' => $db_pass
    );
    $postdata = http_build_query($postvars);

    // Send POST query via cURL
    $postdata = http_build_query($postvars);
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, 'https://' . $hst_hostname . ': ' . $hst_port . '/api/');
    curl_setopt($curl, CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
    curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS, $postdata);
    $answer = curl_exec($curl);

    // Check result
    if($answer == 0) {
        echo "Database has been successfuly created\n";
    } else {
        echo "Query returned error code: " .$answer. "\n";
    }


************************************************
Create Database
************************************************

.. code-block:: php

    <?php

    // Server credentials
    $hst_hostname = 'server.hestiacp.com';
    $hst_username = 'admin';
    $hst_password = 'p4ssw0rd';
    $hst_command = 'v-list-user';

    // Account
    $username = 'demo';
    $format = 'json';

    // Prepare POST query
    $postvars = array(
        'user' => $hst_username,
        'password' => $hst_password,
        'returncode' => $hst_returncode,
        'cmd' => $hst_command,
        'arg1' => $username,
        'arg2' => $format
    );
    $postdata = http_build_query($postvars);

    // Send POST query via cURL
    $postdata = http_build_query($postvars);
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, 'https://' . $hst_hostname . ': ' . $hst_port . '/api/');
    curl_setopt($curl, CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
    curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS, $postdata);
    $answer = curl_exec($curl);

    // Parse JSON output
    $data = json_decode($answer, true);

    // Print result
    print_r($data);


************************************************
List Web Domains
************************************************

.. code-block:: php

    <?php

    // Server credentials
    $hst_hostname = 'server.hestiacp.com';
    $hst_username = 'admin';
    $hst_password = 'p4ssw0rd';
    $hst_command = 'v-list-web-domain';

    // Account
    $username = 'demo';
    $domain = 'demo.hestiacp.com';
    $format = 'json';

    // Prepare POST query
    $postvars = array(
        'user' => $hst_username,
        'password' => $hst_password,
        'returncode' => $hst_returncode,
        'cmd' => $hst_command,
        'arg1' => $username,
        'arg2' => $domain,
        'ar32' => $format
    );
    $postdata = http_build_query($postvars);

    // Send POST query via cURL
    $postdata = http_build_query($postvars);
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, 'https://' . $hst_hostname . ': ' . $hst_port . '/api/');
    curl_setopt($curl, CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
    curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS, $postdata);
    $answer = curl_exec($curl);

    // Parse JSON output
    $data = json_decode($answer, true);

    // Print result
    print_r($data);


************************************************
Delete User Account
************************************************

.. code-block:: php

    <?php

    // Server credentials
    $hst_hostname = 'server.hestiacp.com';
    $hst_username = 'admin';
    $hst_password = 'p4ssw0rd';
    $hst_returncode = 'yes';
    $hst_command = 'v-delete-user';

    // Account
    $username = 'demo';

    // Prepare POST query
    $postvars = array(
        'user' => $hst_username,
        'password' => $hst_password,
        'returncode' => $hst_returncode,
        'cmd' => $hst_command,
        'arg1' => $username
    );
    $postdata = http_build_query($postvars);

    // Send POST query via cURL
    $postdata = http_build_query($postvars);
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, 'https://' . $hst_hostname . ': ' . $hst_port . '/api/');
    curl_setopt($curl, CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
    curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS, $postdata);
    $answer = curl_exec($curl);

    // Parse JSON output
    $data = json_decode($answer, true);

    // Check result
    if($answer == 0) {
        echo "User account has been successfuly deleted\n";
    } else {
        echo "Query returned error code: " .$answer. "\n";
    }


************************************************
Check Username and Password
************************************************

.. code-block:: php

    <?php

    // Server credentials
    $hst_hostname = 'server.hestiacp.com';
    $hst_username = 'admin';
    $hst_password = 'p4ssw0rd';
    $hst_returncode = 'yes';
    $hst_command = 'v-check-user-password';

    // Account
    $username = 'demo';
    $password = 'demopassword';

    // Prepare POST query
    $postvars = array(
        'user' => $hst_username,
        'password' => $hst_password,
        'returncode' => $hst_returncode,
        'cmd' => $hst_command,
        'arg1' => $username,
        'arg2' => $password
    );
    $postdata = http_build_query($postvars);

    // Send POST query via cURL
    $postdata = http_build_query($postvars);
    $curl = curl_init();
    curl_setopt($curl, CURLOPT_URL, 'https://' . $hst_hostname . ': ' . $hst_port . '/api/');
    curl_setopt($curl, CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
    curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
    curl_setopt($curl, CURLOPT_POST, true);
    curl_setopt($curl, CURLOPT_POSTFIELDS, $postdata);
    $answer = curl_exec($curl);

    // Parse JSON output
    $data = json_decode($answer, true);

    // Check result
    if($answer == 0) {
        echo "User account has been successfuly deleted\n";
    } else {
        echo "Query returned error code: " .$answer. "\n";
    }


************************************************
Return Codes
************************************************

.. list-table::
   :header-rows: 1

    *  - VALUE
       - NAME
       - COMMENT
    *  - 0
       - OK
       - Command has been successfuly performed
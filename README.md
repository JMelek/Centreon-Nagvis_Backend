# Centreon-Nagvis Backend (centreonbroker)

A backend connector for NagVis using the Centreon Broker database (centreon_storage`).
This backend enables NagVis maps (including Geomaps) to access host, hostgroup and service information directly from Centreon.

✔ Tested with NagVis 1.9.44
✔ Tested with Centreon 24.10


# 📥 Installation

Copy the backend file to the NagVis backend classes directory:
```bash
cp GlobalBackendcentreonbroker.php /usr/local/nagvis/share/server/core/classes/
```

Set the correct ownership (usually the web server user, e.g. apache):
```bash
chown apache:apache /usr/local/nagvis/share/server/core/classes/GlobalBackendcentreonbroker.php
```


# ⚙️ Configuration

You can use the same user that Centreon stores in `centreon_storage`, or create a dedicated read-only database user.

Create a new backend via the NagVis Web Interface:

Options → Manage Backends → Add Backend
Select backend type: centreonbroker

Example backend configuration:
```ini
[backend_centreonbroker]
backendtype="centreonbroker"
dbhost="127.0.0.1"
dbport=3306
dbname="centreon_storage"
dbuser="centreon"
dbpass="password"
dbinstancename="default"
htmlcgi="/centreon"
```


# 🗺️ Usage

You can set this backend as the global default:
 - **Options → General Configuration → Object Defaults → backend**

Or select it per map:
- **Edit Map → Map Options → Obj. Defaults → backend_id**

This backend supports host and hostgroup filtering, including custom functions added for Geomap usage.


# 📝 Notes

- This backend is designed specifically for Centreon Broker’s database schema.
- It does not use the classic centreon configuration database.
- Additional functions were included to support filtering hosts inside hostgroups (useful for Geomap objects).

  

# How to Install TimescaleDB on Ubuntu 18.04 LTS

### Step 1 :  UPdate the list of available packages and their versions
			sudo apt-get update

### step 2 : remove all the postgres and timescaledb installation if any
			sudo apt-get purge --purge postgres*
			sudo apt-get purge --purge timescaledb*

### step 3: Install PotgresSQl 10.8

#### Installation
			sudo apt install postgresql postgresql-contrib

####  Switch over to the postgres account on your server by typing:
			sudo -i -u postgres

####  Set PostgreSQL admin user’s password:
			psql -c "alter user postgres with password 'xyz@scs'"

###  Step 4: Install TimescaleDB

####  Add PPA :
			sudo add-apt-repository ppa:timescale/timescaledb-ppa
			sudo apt-get update

####  Installation :
			sudo apt install timescaledb-postgresql-10

####  Edit postgresql.conf to load necessary TImescaleDB libraries:
			sudo vim  /etc/postgresql/10/main/postgresql.conf

####  Find the line below and change the value as shown (uncomment if needed):
			shared_preload_libraries = 'timescaledb'

####  Restart postgresql service after saving the changes
		  sudo service postgresql restart

### Step 5:  Test TimescaleDB installation
      sudo -i -u postgres
      psql
      CREATE database test_db;
      \c test_db
      CREATE EXTENSION IF NOT EXISTS timescaledb CASCADE;


### Now you can connect directly to the newly created database:
      psql -U postgres -h localhost -d test_db

will ask for password type : xyz@scs (or whatever you have use above)

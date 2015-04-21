clvsol_odoo_clvhealth
=====================

* ubun14

    ::

        cd '/opt/openerp/clvhealth'
        gzip -d clvhealth_pro_2015-03-23a.sql.gz
        dropdb -i clvhealth_dev -U postgres
        createdb -O openuser -E UTF8 -T template0 clvhealth_dev -U postgres
        psql -f clvhealth_pro_2015-03-23a.sql -d clvhealth_dev -h localhost -p 5432 -q -U postgres

        cd '/opt/openerp/clvhealth'
        pg_dump clvhealth_dev -Fp -U postgres -h localhost -p 5432 > clvhealth_dev.sql
        mv clvhealth_dev.sql clvhealth_dev_2015-03-23a.sql
        gzip clvhealth_dev_2015-03-23a.sql

    ::

        cd '/opt/openerp/clvhealth'
        dropdb -i clvhealth_dev -U postgres
        createdb -O openuser -E UTF8 -T template0 clvhealth_dev -U postgres
        psql -f clvhealth_dev_2015-03-23a.sql -d clvhealth_dev -h localhost -p 5432 -q -U postgres

    ::

        cd cd '/opt/openerp/clvsol_odoo_clvhealth/project'
        python install.py

* tkl-lamp-odoo-health-tst

    ::
        
        git clone https://bitbucket.org/cvercelino/clvsol_odoo_addons /opt/openerp/clvsol_odoo_addons --branch 8.0-priv
        chown -R openerp:openerp /opt/openerp/clvsol_odoo_addons

    ::
        
        git clone https://bitbucket.org/cvercelino/clvsol_odoo_addons_l10n_br /opt/openerp/clvsol_odoo_addons_l10n_br --branch 8.0-priv
        chown -R openerp:openerp /opt/openerp/clvsol_odoo_addons_l10n_br

    ::
        
        git clone https://bitbucket.org/cvercelino/clvsol_odoo_addons_clvhealth /opt/openerp/clvsol_odoo_addons_clvhealth --branch 8.0
        chown -R openerp:openerp /opt/openerp/clvsol_odoo_addons_clvhealth

    ::

        cd '/opt/openerp/clvhealth'
        gzip -d clvhealth_dev_2015-04-11b_063.sql.gz
        su postgres
        dropdb -i clvhealth_tst -U postgres
        createdb -O openuser -E UTF8 -T template0 clvhealth_tst -U postgres
        psql -f clvhealth_dev_2015-04-11b_063.sql -d clvhealth_tst -h localhost -p 5432 -q -U postgres
        exit

    ::
        
        cd /opt/openerp/odoo
        su openerp
        ./openerp-server -c openerp-server-man.conf

	::

		cd /opt/openerp
		su openerp
		cd /opt/openerp/odoo
		git pull
		cd /opt/openerp/clvsol_odoo_addons
		git pull
		cd /opt/openerp/clvsol_odoo_addons_l10n_br
		git pull
		cd /opt/openerp/clvsol_odoo_addons_clvhealth
		git pull
		exit

* tkl-lamp-odoo-health-pro

    ::
        
        git clone https://bitbucket.org/cvercelino/clvsol_odoo_addons /opt/openerp/clvsol_odoo_addons --branch 8.0-priv
        chown -R openerp:openerp /opt/openerp/clvsol_odoo_addons

    ::
        
        git clone https://bitbucket.org/cvercelino/clvsol_odoo_addons_l10n_br /opt/openerp/clvsol_odoo_addons_l10n_br --branch 8.0-priv
        chown -R openerp:openerp /opt/openerp/clvsol_odoo_addons_l10n_br

    ::
        
        git clone https://bitbucket.org/cvercelino/clvsol_odoo_addons_clvhealth /opt/openerp/clvsol_odoo_addons_clvhealth --branch 8.0
        chown -R openerp:openerp /opt/openerp/clvsol_odoo_addons_clvhealth

    ::

        cd '/opt/openerp/clvhealth'
        gzip -d clvhealth_pro_2015-03-30a.sql.gz
        su postgres
        dropdb -i clvhealth_pro -U postgres
        createdb -O openuser -E UTF8 -T template0 clvhealth_pro -U postgres
        psql -f clvhealth_pro_2015-03-30a.sql -d clvhealth_pro -h localhost -p 5432 -q -U postgres
        exit

    ::

        cd '/opt/openerp/clvhealth'
        pg_dump clvhealth_pro -Fp -U postgres -h localhost -p 5432 > clvhealth_pro.sql
        mv clvhealth_pro.sql clvhealth_pro_2015-03-30a.sql
        gzip clvhealth_pro_2015-03-30a.sql

    ::
        
        cd /opt/openerp/odoo
        su openerp
        ./openerp-server -c openerp-server-man.conf

* /opt/openerp/odoo/openerp-server.conf and /opt/openerp/odoo/openerp-server-man.conf

    ::

        addons_path = /opt/openerp/odoo/addons,/opt/openerp/oca_server_tools,/opt/openerp/clvsol_odoo_addons,/opt/openerp/clvsol_odoo_addons_l10n_br,/opt/openerp/clvsol_odoo_addons_clvhealth

* Commands

    ::

        /opt/openerp/openerp.init stop
        /opt/openerp/openerp.init start

    ::
        
        cd /opt/openerp/odoo
        ./openerp-server -c openerp-server-8.0-clvhealth.conf

    ::

        cd /opt/openerp/clvsol_odoo_clvhealth/doc
        make clean
        make html
        
    ::

        cd /opt/openerp/clvsol_odoo_clvhealth/project
        python install.py

.. toctree::
   :maxdepth: 2

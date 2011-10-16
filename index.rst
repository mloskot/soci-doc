.. SOCI documentation master file, created by
   sphinx-quickstart on Mon Sep 26 00:03:19 2011.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

SOCI is a database access library for C++ that makes the illusion of 
*embedding* SQL queries in the regular C++ code, staying entirely 
within the Standard C++.

The idea is to provide C++ programmers a way to access SQL databases 
in the most natural and intuitive way. If you find existing libraries 
too difficult for your needs or just distracting, SOCI can be a good alternative.

The simplest motivating code example for the SQL query that is supposed to retrieve
a single row is:

.. code-block:: cpp

    int id = ...;
    string name;
    int salary;

    sql << "select name, salary from persons where id = " << id,
           into(name), into(salary);

and the following benefits from extensive support for object-relational mapping:

.. code-block:: cpp

    int id = ...;
    Person p;

    sql << "select first_name, last_name, date_of_birth "
           "from persons where id = " << id,
           into(p);

Integration with STL is also supported:

.. code-block:: cpp

    Rowset<string> rs = (sql.prepare << "select name from persons");
    copy(rs.begin(), rs.end(), ostream_iterator<string>(cout, "\n"));

SOCI offers also extensive integration with Boost datatypes (optional, tuple and fusion) 
and flexible support for user-defined datatypes.

Starting from its 2.0.0 release, SOCI uses the plug-in architecture for backends - this 
allows to target various database servers. Currently (3.0.0), the following database 
servers are supported:

* MySQL
* Oracle
* PostgreSQL

Other (oficially unsupported yet) backends exist in the Git repository (See :ref:`Download` page):

* Firebird.
* ODBC
* SQLite

The intent of the library is to cover as many database technologies as possible.
For this, the project has to rely on volunteer contributions from other programmers, 
who have expertise with the existing database interfaces and would like to help 
writing dedicated backends. If you are interested in participating, please
contact the project admin. See :ref:`People` for details.


License
------------------------------------------------------------------------------

The SOCI library is distributed under the terms of the Boost Software License.
See :ref:`License` for a copy.

Indices and tables
==================

* :ref:`search`

.. toctree::
   :maxdepth: 2
   :hidden:

   news
   features
   download
   tutorial
   documentation
   faq
   people
   support
   articles
   links
   copyright

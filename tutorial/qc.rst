Data quality control process
=============================

**BDMS** do not only support data entering and access, it also incorporate a data validation workflow that brings data to publication.

1. Data stages
----------------

The validation workflow is composed by **four data stages**:

- **Editing**: data are in editing and considered in draft; this is generally done by companies.
- **Scientific check**: data are undergoing a scientific control to ensure the correctness of technical information (this is generally done by geologists).
- **Validation**: data are considered from a more administrative and legal point of view to validate their quality (this is generally done by administration).
- **Publication**: data are considered to be published as public data.

.. thumbnail:: ../images/quality_process.png
    :width: 50%
    :align: center

2. User roles
---------------

Accordingly, to control the authorization on the four data stages defined above, the BDMS defines five **user roles**:

- **Data viewer** (VIEWER): is enabled to view data.
- **Data producer** (EDITOR): is enabled to create boreholes and enter data.
- **Data controller** (CONTROLLER): is enabled to validate, or request for modifications, to submitted data.
- **Data validator** (VALIDATOR): is enabled to validate, or request for modifications, to controlled data.
- **System administrator** (PUBLISHER): is enable to decided to make public the data or to keep for authenticated users only.

3. Workgroups
---------------

These *roles* applies to **workgroups** . A *workgroup* is a dedicated working area (for example to handle data from a specific project or a specific company). Data in this area can be accessed, depending on specific roles, only by workgroup's members. 

.. thumbnail:: ../images/workgroups.png
    :width: 50%
    :align: center

*Admin* users can manage users, workgroups and roles using the Admin interface activated by the Setting menu.

.. thumbnail:: ../images/user_roles.png
    :width: 100%
    :align: center




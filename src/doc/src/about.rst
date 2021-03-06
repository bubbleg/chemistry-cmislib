..
   Licensed to the Apache Software Foundation (ASF) under one
   or more contributor license agreements.  See the NOTICE file
   distributed with this work for additional information
   regarding copyright ownership.  The ASF licenses this file
   to you under the Apache License, Version 2.0 (the
   "License"); you may not use this file except in compliance
   with the License.  You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing,
   software distributed under the License is distributed on an
   "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
   KIND, either express or implied.  See the License for the
   specific language governing permissions and limitations
   under the License.

About Apache Chemistry cmislib
=============================
The goal of this project is to create a CMIS client for Python that can be used to work with any CMIS-compliant repository.

The library is being developed with the following guidelines:
 * Developers using this API should be able to work with CMIS domain objects without having to worry about the underlying implementation details.
 * The library will use the Resftul AtomPub Binding.
 * The library will conform to the `CMIS spec <http://docs.oasisopen.org/cmis/CMIS/v1.0/cd06/cmis-spec-v1.0.pdf>`_ as closely as possible. Several public CMIS repositories are being used to test the API. 
 * The library should have no hard-coded URL's. It should be able to get everything it needs regarding how to work with the CMIS service from the CMIS service URL response and subsequent calls.
 * There shouldn't have to be a vendor-specific version of this library. The goal is for it to be interoperable with CMIS-compliant providers.

Quick Example
-------------
This should give you an idea of how easy and natural it is to work with the API:
  >>> cmisClient = cmislib.CmisClient('http://localhost:8080/alfresco/cmisatom', 'admin', 'admin')
  >>> repo = cmisClient.defaultRepository
  >>> rootFolder = repo.rootFolder
  >>> children = rootFolder.getChildren()
  >>> newFolder = rootFolder.createFolder('testDeleteFolder folder')
  >>> props = newFolder.properties
  >>> newFolder.delete()

To-Do's
-------
Miscellaneous
 * createDocumentFromSource
 * getProperties filter
 * getContentStream stream id

Renditions
 * getRenditions

Unfiling/multifiling support
 * createDocument without a parent folder (unfiled)

  * The spec does not yet support this. Although the spec does say that a folder ID is optional, it does not specify which URL to post the unfiled document to.

Policies
 * Policy object
 * createPolicy
 * applyPolicy
 * removePolicy
 * getAppliedPolicies

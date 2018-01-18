===================================
ZenPacks.sungard.EventCustomization
===================================


Description
-----------

This ZenPack is to deploy event classes and their customizations, specific to Sungard.

Some rules must be followed to ensure that both installation and removal is trouble-free:

* Only Sungard-specific events should be put in this ZenPack
* Other events from the Zenoss core product or other ZenPacks must *not* be included
* This README *must* be updated accurately whenever changes are made, otherwise any potential
  rollback operations may be misunderstood
* This ZenPack may also include auto-ticketing rules; they will only be installed on a MOM.
* The release number *must* be changed whenever changes are made.  This is to ensure that a 
  previous release can be reinstalled as part of a roll-back mechanism.
* If event classes specified here are subclasses of events provided by another ZenPack, then
  that ZenPack should be made a prerequisite in this ZenPack.  For example, adding an event class
  /vSphere/JustEnergySimplivity requires the /vSphere class which is provided in
  ZenPacks.zenoss.vSphere.  



Naming Conventions
------------------

To maintain consistency and compatibility with other elements of Zenoss that manipulate events, it
is important to adhere to naming conventions.

* Customer-specific event classes should start with the name of the customer and also include the
  type of event that is being customized.  For example, a Just Energy device, which appears in the 
  Zenoss System "/Customers/F-J/JUST ENERGY CORP/  that addresses events with "Simplivity",
  might be "JustEnergySimplivity".  Note the capitalization at the start of each word.
  This is to make customer-specific auto-ticketing easier by enabling a search for an event class
  that "startswith" <customer name>.
* Event class mappings (also known as instances) should have names that match the eventClassKey.
* Any default mappings created must be called defaultmapping, otherwise the Sungard transform
  update process implemented with the updatetransforms.sh script, will fail.  Any default mapping 
  transform managed by updatetransforms.sh must also adhere to this naming rule




Event Classes
=============

* /vSphere/SungardCloudPlatformZerto

  - no event class transform
  - defaultmapping with:

    + eventClassKey of defaultmapping
    + Rule
    + Regex
    + Example
    + Transform
    + Sequence number

* /vSphere/JustEnergySimplivity

  - no event class transform
  - defaultmapping with:

    + eventClassKey of defaultmapping
    + Rule
    + Regex
    + Example
    + No Transform
    + Sequence number



Auto-ticketing rules
====================

Some event customization will be a prerequisite for automatically creating incident tickets in
Service Now.  Such rules are held on a MOM Zenoss server under /opt/zenoss/etc/auto-ticketing-rules.
If a rule is included in this ZenPack under the auto-ticketing-rules directory, then, when the
ZenPack is installed on a MOM then any rules from the ZenPack will replace the existing rule.
The existing rule will be backed up on the MOM under the name backup_<ZP and rel>_<date>_<existing rule name>;
such file names will not be read by the getRuleFileNames procedure in AutoTicketRulesProcessor.py in the
ZenPacks.sungard.EventEnrichment ZenPack.

How do we keep ZenPack rules and MOM rules in synch?





Requirements & Dependencies
===========================

* Zenoss Versions Supported:  4.x
* External Dependencies: 
* ZenPack Dependencies: 

  - ZenPacks.zenoss.vSphere (provides base /vSphere event class)


ZenPack installation
======================

This ZenPack can be installed from the .egg file using either the GUI or the
zenpack command line. 

To install in development mode:
Install from /code/ZenPacks with::
  zenpack --link --install ZenPacks.sungard.EventCustomization

Installation Notes 
------------------

  - Restart zenoss entirely after installation       or 
  - For Zenoss Core 3.x and 4.x, restart zenhub and zopectl
  - For Zenoss Service Dynamics, restart zenoss entirely after installation
  - For Zenoss 5, restart zenoss entirely after installation


* Configuration: 

  - Add the blah modeler plugin to the /Server/Linux/Blah device class


Limitations and Troubleshooting
===============================



Change History
==============
* 1.0.0
   - Initial Release
   - /vSphere/SungardCloudPlatformZerto
   - /vSphere/JustEnergySimplivity


* 1.0.1
   - 

Screenshots
===========

See the screenshots directory.


Acknowledgements
================

This ZenPack has been developed with the help of ....


---
Description: An abstract class that represents port runtime data collected by an Ethernet switch extension.
ms.assetid: bc41ad1d-e7ab-4d04-96a8-26eb68ea6601
title: Msvm\_EthernetPortData class
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# Msvm\_EthernetPortData class

An abstract class that represents port runtime data collected by an Ethernet switch extension. All Ethernet port data classes must derive from this abstract class.

The following syntax is simplified Managed Object Format (MOF) code, and it includes all of the inherited properties.

## Syntax

``` syntax
[Abstract, Provider("VmmsWmiInstanceAndMethodProvider"), AMENDMENT]
class Msvm_EthernetPortData : CIM_ManagedElement
{
  string InstanceID;
  string Caption;
  string Description;
  string ElementName;
  string SystemCreationClassName;
  string SystemName;
  string DeviceCreationClassName = "Msvm_EthernetSwitchPort";
  string DeviceID;
  string CreationClassName;
  string Name;
};
```

## Members

The **Msvm\_EthernetPortData** class has these types of members:

-   [Properties](#properties)

### Properties

The **Msvm\_EthernetPortData** class has these properties.

<dl> <dt>

**Caption**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> </dl>

A short description of the object. This property is inherited from [**CIM\_ManagedElement**](https://msdn.microsoft.com/library/mt432218).

</dd> <dt>

**CreationClassName**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**Key**](https://msdn.microsoft.com/library/aa392157), [**MaxLen**](https://msdn.microsoft.com/library/aa393650) (256)
</dt> </dl>

The name of the subclass used in the creation of this port data instance.

</dd> <dt>

**Description**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> </dl>

A description of the object. This property is inherited from [**CIM\_ManagedElement**](https://msdn.microsoft.com/library/mt432218).

</dd> <dt>

**DeviceCreationClassName**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**Key**](https://msdn.microsoft.com/library/aa392157), [**Propagated**](https://msdn.microsoft.com/library/aa393650) ("[**CIM\_LogicalDevice**](cim-logicaldevice.md).**CreationClassName**"), [**MaxLen**](https://msdn.microsoft.com/library/aa393650) (256)
</dt> </dl>

The scoping system's creation class name. This property is always set to "Msvm\_EthernetSwitchPort".

</dd> <dt>

**DeviceID**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**Key**](https://msdn.microsoft.com/library/aa392157), [**Propagated**](https://msdn.microsoft.com/library/aa393650) ("[**CIM\_LogicalDevice**](cim-logicaldevice.md).**DeviceID**"), [**MaxLen**](https://msdn.microsoft.com/library/aa393650) (64)
</dt> </dl>

The Device ID of the port that scopes this port data instance.

</dd> <dt>

**ElementName**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> </dl>

A display name for the object. This property is inherited from [**CIM\_ManagedElement**](https://msdn.microsoft.com/library/mt432218).

</dd> <dt>

**InstanceID**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: **Key**
</dt> </dl>

Uniquely identifies an instance of this class. This property is inherited from [**CIM\_ManagedElement**](https://msdn.microsoft.com/library/mt432218).

</dd> <dt>

**Name**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**Key**](https://msdn.microsoft.com/library/aa392157), [**MaxLen**](https://msdn.microsoft.com/library/aa393650) (256)
</dt> </dl>

A string that uniquely identifies this port data instance within the scope of the switch and port.

</dd> <dt>

**SystemCreationClassName**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**Key**](https://msdn.microsoft.com/library/aa392157), [**Propagated**](https://msdn.microsoft.com/library/aa393650) ("[**CIM\_System**](cim-system.md).**CreationClassName**"), [**MaxLen**](https://msdn.microsoft.com/library/aa393650) (256)
</dt> </dl>

The scoping system's creation class name.

</dd> <dt>

**SystemName**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: [**Key**](https://msdn.microsoft.com/library/aa392157), [**Propagated**](https://msdn.microsoft.com/library/aa393650) ("[**CIM\_System**](cim-system.md).**Name**"), [**MaxLen**](https://msdn.microsoft.com/library/aa393650) (256)
</dt> </dl>

The name of the virtual switch that scopes this port data instance.

</dd> </dl>

## Requirements



|                                     |                                                                                                         |
|-------------------------------------|---------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 8 \[desktop apps only\]<br/>                                                              |
| Minimum supported server<br/> | Windows Server 2012 \[desktop apps only\]<br/>                                                    |
| Namespace<br/>                | Root\\Virtualization\\V2<br/>                                                                     |
| MOF<br/>                      | <dl> <dt>WindowsVirtualization.V2.mof</dt> </dl> |
| DLL<br/>                      | <dl> <dt>Vmms.exe</dt> </dl>                     |



 

 




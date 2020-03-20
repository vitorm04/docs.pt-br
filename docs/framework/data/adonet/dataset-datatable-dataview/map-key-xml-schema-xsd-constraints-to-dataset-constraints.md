---
title: Mapear restrições de esquema XML (XSD) chave para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 5ebf333b065157fa9497cc1471a45698663638e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150929"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapear restrições de esquema XML (XSD) chave para restrições de DataSet
Em um esquema, você pode especificar uma restrição de chave em um elemento ou atributo usando o **elemento-chave.** O elemento ou atributo no qual uma restrição de chave é especificada deve ter valores únicos em qualquer instância de esquema e não pode ter valores nulos.  
  
 A restrição de chave é semelhante à restrição única, exceto que a coluna na qual uma restrição de chave é definida não pode ter valores nulos.  
  
 A tabela a seguir descreve os **atributos msdata** que você pode especificar no **elemento-chave.**  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Se este atributo for especificado, seu valor será usado como nome de restrição. Caso contrário, o atributo **nome** fornece o valor do nome de restrição.|  
|**msdata:PrimaryKey**|Se `PrimaryKey="true"` estiver presente, a propriedade de restrição **IsPrimaryKey** é definida como **true,** tornando-a uma chave primária. A propriedade Da coluna **AllowDBNull** é definida como **falsa,** porque as chaves primárias não podem ter valores nulos.|  
  
 Ao converter esquema no qual uma restrição de chave é especificada, o processo de mapeamento cria uma restrição única na tabela com a propriedade da coluna **AllowDBNull** definida como **falsa** para cada coluna na restrição. A propriedade **IsPrimaryKey** da restrição exclusiva também é definida `msdata:PrimaryKey="true"` como **falsa,** a menos que você tenha especificado no **elemento-chave.** Isto é idêntico a uma restrição única `PrimaryKey="true"`no esquema em que .  
  
 No exemplo do esquema a seguir, o **elemento-chave** especifica a restrição de chave no elemento **CustomerID.**  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 O **elemento-chave** especifica que os valores do elemento filho **CustomerID** do elemento **Clientes** devem ter valores únicos e não podem ter valores nulos. Ao traduzir o esquema de definição de Esquema XML (XSD), o processo de mapeamento cria a seguinte tabela:  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 O mapeamento xml schema também cria uma **Restrição Única** na coluna <xref:System.Data.DataSet> **CustomerID,** como mostrado no seguinte . (Para simplificar, apenas propriedades relevantes são mostradas.)  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 No **Conjunto de Dados** gerado, a propriedade **IsPrimaryKey** da **UniqueConstraint** é definida `msdata:PrimaryKey="true"` como **true** porque o esquema especifica no **elemento-chave.**  
  
 O valor da propriedade **ConstraintName** da **UniqueConstraint** no **DataSet** é o valor do atributo **msdata:ConstraintName** especificado no **elemento-chave** no esquema.  
  
## <a name="see-also"></a>Confira também

- [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Gerar relações de DataSet do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)

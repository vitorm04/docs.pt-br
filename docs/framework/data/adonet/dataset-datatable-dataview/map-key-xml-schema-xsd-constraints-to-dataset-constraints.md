---
title: "Restrições de esquema XML (XSD) às restrições de conjunto de dados de chave de mapa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6b999e6b1d6d73f107b7e1f4cb0d7e14c099a1f6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Restrições de esquema XML (XSD) às restrições de conjunto de dados de chave de mapa
Em um esquema, você pode especificar uma restrição de chave em um elemento ou atributo usando o **chave** elemento. O elemento ou atributo no qual uma restrição de chave for especificada deve ter valores exclusivos em qualquer instância do esquema e não pode ter valores nulos.  
  
 A restrição de chave é semelhante a restrição unique, exceto que a coluna na qual é definida uma restrição de chave não pode ter valores nulos.  
  
 A tabela a seguir descreve o **msdata** atributos que você pode especificar o **chave** elemento.  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Se esse atributo for especificado, seu valor é usado como o nome da restrição. Caso contrário, o **nome** atributo fornece o valor do nome da restrição.|  
|**msdata:PrimaryKey**|Se `PrimaryKey="true"` estiver presente, o **IsPrimaryKey** restrição está definida como **true**, tornando uma chave primária. O **AllowDBNull** coluna está definida como **false**, porque as chaves primárias não podem ter valores nulos.|  
  
 Na conversão do esquema no qual uma restrição de chave for especificada, o processo de mapeamento cria uma restrição exclusiva na tabela com o **AllowDBNull** propriedade column definida como **false** para cada coluna a restrição. O **IsPrimaryKey** propriedade da restrição unique também é definida como **false** , a menos que você especificou `msdata:PrimaryKey="true"` no **chave** elemento. Isso é idêntico de uma restrição exclusiva no esquema no qual `PrimaryKey="true"`.  
  
 No exemplo de esquema a seguir, o **chave** elemento Especifica a restrição de chave no **CustomerID** elemento.  
  
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
  
 O **chave** elemento Especifica que os valores da **CustomerID** elemento filho do **clientes** elemento deve ter valores exclusivos e não pode ter valores nulos. Converter o esquema de linguagem XSD de definição de esquema XML, o processo de mapeamento cria a tabela a seguir:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 O mapeamento de esquema XML também cria um **UniqueConstraint** no **CustomerID** coluna, conforme mostrado no exemplo a seguir <xref:System.Data.DataSet>. (Para manter a simplicidade, somente as propriedades relevantes são mostradas.)  
  
```  
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
  
 No **conjunto de dados** que é gerado, o **IsPrimaryKey** propriedade o **UniqueConstraint** é definido como **true** porque o esquema Especifica `msdata:PrimaryKey="true"` no **chave** elemento.  
  
 O valor da **ConstraintName** propriedade do **UniqueConstraint** no **conjunto de dados** é o valor da **msdata:ConstraintName** o atributo especificado no **chave** elemento no esquema.  
  
## <a name="see-also"></a>Consulte também  
 [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Gerando relações de conjunto de dados do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

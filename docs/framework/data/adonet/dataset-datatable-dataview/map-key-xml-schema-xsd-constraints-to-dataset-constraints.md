---
title: Mapear restrições de esquema XML (XSD) chave para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 46a980f06198c6f06bb13824c65cfb5309eec154
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034223"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapear restrições de esquema XML (XSD) chave para restrições de DataSet
Em um esquema, você pode especificar uma restrição de chave em um elemento ou atributo usando o **chave** elemento. O elemento ou atributo no qual uma restrição de chave for especificada deve ter valores exclusivos em qualquer instância do esquema e não pode ter valores nulos.  
  
 A restrição de chave é semelhante a restrição unique, exceto que a coluna na qual uma restrição de chave é definida não é possível ter valores nulos.  
  
 A tabela a seguir descreve o **msdata** atributos que você pode especificar o **chave** elemento.  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Se esse atributo for especificado, seu valor é usado como o nome da restrição. Caso contrário, o **nome** atributo fornece o valor do nome da restrição.|  
|**msdata:PrimaryKey**|Se `PrimaryKey="true"` estiver presente, o **IsPrimaryKey** restrição estiver definida como **true**, tornando-o uma chave primária. O **AllowDBNull** coluna estiver definida como **falso**, porque as chaves primárias não podem ter valores nulos.|  
  
 Na conversão de esquema no qual uma restrição de chave for especificada, o processo de mapeamento cria uma restrição exclusiva na tabela com o **AllowDBNull** propriedade column definida como **falso** para cada coluna a restrição. O **IsPrimaryKey** propriedade da restrição exclusiva também é definida como **falso** , a menos que você especificou `msdata:PrimaryKey="true"` no **chave** elemento. Isso é idêntico de uma restrição exclusiva no esquema no qual `PrimaryKey="true"`.  
  
 No exemplo de esquema a seguir, o **chave** elemento Especifica a restrição de chave sobre o **CustomerID** elemento.  
  
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
  
 O **chave** elemento Especifica que os valores da **CustomerID** elemento filho do **clientes** elemento deve ter valores exclusivos e não pode ter valores nulos. Na conversão do esquema de (XSD) de linguagem de definição de esquema XML, o processo de mapeamento cria a tabela a seguir:  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 O mapeamento de esquema XML também cria uma **UniqueConstraint** na **CustomerID** coluna, conforme mostrado no seguinte <xref:System.Data.DataSet>. (Para simplificar, somente as propriedades relevantes são exibidas.)  
  
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
  
 No **DataSet** que é gerado, o **IsPrimaryKey** propriedade do **UniqueConstraint** é definido como **true** porque o esquema Especifica `msdata:PrimaryKey="true"` no **chave** elemento.  
  
 O valor da **ConstraintName** propriedade do **UniqueConstraint** no **conjunto de dados** é o valor da **msdata:ConstraintName** atributo especificado na **chave** elemento no esquema.  
  
## <a name="see-also"></a>Consulte também

- [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Gerando relações de conjunto de dados do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

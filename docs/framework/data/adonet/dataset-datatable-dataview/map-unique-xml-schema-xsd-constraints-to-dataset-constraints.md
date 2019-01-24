---
title: Mapear restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: c35dcadfb40fcb73104af7ee7456e64a68c9e023
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677052"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapear restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados
Em um esquema XSD (linguagem) de definição de esquema XML, o **exclusivo** elemento Especifica a restrição de exclusividade em um elemento ou atributo. No processo de conversão de um esquema XML em um esquema relacional, a restrição unique especificada em um elemento ou atributo no esquema XML é mapeada para uma restrição exclusiva na <xref:System.Data.DataTable> nas correspondentes <xref:System.Data.DataSet> que é gerado.  
  
 A tabela a seguir descreve o **msdata** atributos que você pode especificar o **exclusivo** elemento.  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Se esse atributo for especificado, seu valor é usado como o nome da restrição. Caso contrário, o **nome** atributo fornece o valor do nome da restrição.|  
|**msdata:PrimaryKey**|Se `PrimaryKey="true"` está presente na **exclusivo** elemento, uma restrição exclusiva é criada com o **IsPrimaryKey** propriedade definida como **true**.|  
  
 O exemplo a seguir mostra um esquema XML que usa o **exclusivo** elemento para especificar uma restrição de exclusividade.  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 O **exclusivos** elemento no esquema Especifica que, para todos os **clientes** elementos em um documento de instância, o valor da **CustomerID** elemento filho deve ser exclusivo. Na construção do **conjunto de dados**, o processo de mapeamento lê esse esquema e gera a tabela a seguir:  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 O processo de mapeamento também cria uma restrição exclusiva na **CustomerID** coluna, conforme mostrado no seguinte **conjunto de dados**. (Para simplificar, somente as propriedades relevantes são exibidas.)  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 No **DataSet** que é gerado, o **IsPrimaryKey** estiver definida como **False** para a restrição exclusiva. O **exclusivos** propriedade na coluna indica que o **CustomerID** valores de coluna devem ser exclusivos (mas podem ser uma referência nula, conforme especificado pelo **AllowDBNull** propriedade da coluna).  
  
 Se você modificar o esquema e defina o cabeçalho opcional **msdata:PrimaryKey** valor ao atributo **verdadeiro**, a restrição exclusiva será criada na tabela. O **AllowDBNull** coluna estiver definida como **falso**e o **IsPrimaryKey** propriedade da restrição definida como **True**, tornando assim o **CustomerID** coluna uma coluna de chave primária.  
  
 Você pode especificar uma restrição exclusiva em uma combinação de elementos ou atributos no esquema XML. O exemplo a seguir demonstra como especificar que uma combinação de **CustomerID** e **CompanyName** valores devem ser exclusivos para todos os **clientes** em qualquer instância por Adicionar outra **xs:field** elemento no esquema.  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 Essa é a restrição que é criada no resultante **conjunto de dados**.  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Consulte também
- [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Gerando relações de conjunto de dados do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

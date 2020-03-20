---
title: Mapear de restrições de esquema XML (XSD) exclusivas para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150838"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapear de restrições de esquema XML (XSD) exclusivas para restrições de DataSet
Em um esquema de definição de Esquema XML (XSD), o elemento **único** especifica a restrição de exclusividade em um elemento ou atributo. No processo de tradução de um Esquema XML em um esquema relacional, a restrição única especificada em um elemento ou atributo <xref:System.Data.DataTable> no <xref:System.Data.DataSet> Esquema XML é mapeada para uma restrição única no correspondente gerado.  
  
 A tabela a seguir descreve os **atributos msdata** que você pode especificar no elemento **único.**  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|Se este atributo for especificado, seu valor será usado como nome de restrição. Caso contrário, o atributo **nome** fornece o valor do nome de restrição.|  
|**msdata:PrimaryKey**|Se `PrimaryKey="true"` estiver presente no elemento **único,** uma restrição única será criada com a propriedade **IsPrimaryKey** definida como **true**.|  
  
 O exemplo a seguir mostra um Esquema XML que usa o elemento **exclusivo** para especificar uma restrição de exclusividade.  
  
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
  
 O elemento **único** no esquema especifica que, para todos os elementos **clientes** em uma instância de documento, o valor do elemento filho **CustomerID** deve ser único. Na construção do **DataSet,** o processo de mapeamento lê este esquema e gera a seguinte tabela:  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 O processo de mapeamento também cria uma restrição única na coluna **CustomerID,** como mostrado no **Conjunto de Dados**a seguir . (Para simplificar, apenas propriedades relevantes são mostradas.)  
  
```text  
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
  
 No **Conjunto de dados** gerado, a propriedade **IsPrimaryKey** é definida como **False** para a restrição única. A propriedade **única** na coluna indica que os valores da coluna **CustomerID** devem ser únicos (mas podem ser uma referência nula, conforme especificado pela propriedade **AllowDBNull** da coluna).  
  
 Se você modificar o esquema e definir o valor de atributo **msdata:PrimaryKey** para **True,** a restrição única será criada na tabela. A propriedade da coluna **AllowDBNull** está definida como **False**, e a propriedade **IsPrimaryKey** da restrição definida como **True,** tornando assim a coluna **CustomerID** uma coluna de chave primária.  
  
 Você pode especificar uma restrição única em uma combinação de elementos ou atributos no Esquema XML. O exemplo a seguir demonstra como especificar que uma combinação de valores **De CustomerID** e **CompanyName** deve ser única para todos **os Clientes** em qualquer instância, adicionando outro elemento **xs:campo** no esquema.  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 Esta é a restrição criada no **Conjunto de Dados**resultante .  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>Confira também

- [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Gerar relações de DataSet do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)

---
title: Relações e restrições de esquema XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 990ae2eef8d9fbd28472494c989ae9ecca34251d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119776"
---
# <a name="xml-schema-constraints-and-relationships"></a>Relações e restrições de esquema XML
Em um esquema XSD (linguagem) de definição de esquema XML, você pode especificar restrições (exclusivos, restrições de chave e keyref) e relacionamentos (usando o **msdata:Relationship** anotação). Este tópico explica como as restrições e relações especificadas em um esquema XML são interpretadas para gerar o <xref:System.Data.DataSet>.  
  
 Em geral, em um esquema XML, especifique o **msdata:Relationship** anotação se você quiser gerar somente os relacionamentos na **conjunto de dados**. Para obter mais informações, consulte [gerando relações de conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md). Você especifica restrições (exclusiva, chave e keyref) se você quiser gerar restrições na **conjunto de dados**. Observe que as restrições de chave e keyref também são usadas para gerar relações, conforme explicado mais adiante neste tópico.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Gerando uma relação de chave e as restrições de keyref  
 Em vez de especificar o **msdata:Relationship** anotação, você pode especificar restrições de chave e keyref, que são usadas durante o processo de mapeamento de esquema XML para gerar não apenas as restrições, mas também a relação em que o  **Conjunto de dados**. No entanto, se você especificar `msdata:ConstraintOnly="true"` no **keyref** elemento, o **conjunto de dados** incluirá somente as restrições e não incluirá a relação.  
  
 O exemplo a seguir mostra um esquema XML que inclui **ordem** e **OrderDetail** elementos, que não estão aninhados. O esquema também especifica as restrições de chave e keyref.  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 O **DataSet** que é gerado durante o esquema XML que inclui o processo de mapeamento a **ordem** e **OrderDetail** tabelas. Além disso, o **conjunto de dados** inclui relações e restrições. O exemplo a seguir mostra essas relações e restrições. Observe que o esquema não especificar o **msdata:Relationship** anotação; em vez disso, as restrições de chave e keyref são usadas para gerar a relação.  
  
```  
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 No exemplo anterior do esquema, o **ordem** e **OrderDetail** elementos não estão aninhados. No exemplo de esquema a seguir, esses elementos são aninhados. No entanto, não há **msdata:Relationship** anotação é especificada; portanto, uma relação implícita é assumida. Para obter mais informações, consulte [implícita relações entre aninhados esquema elementos do mapa](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md). O esquema também especifica as restrições de chave e keyref.  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 O **conjunto de dados** resultante do processo de mapeamento de esquema XML inclui duas tabelas:  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 O **DataSet** também inclui as duas relações (com base na **msdata:relationship** anotação e o outro com base nas restrições de chave e keyref) e várias restrições. O exemplo a seguir mostra as relações e restrições.  
  
```  
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 Se uma restrição de keyref referente a uma tabela aninhada contém o **msdata:IsNested = "true"** anotação, o **conjunto de dados** criará uma relação aninhada com base na restrição keyref e o restrição de chave exclusiva/relacionada.  
  
## <a name="see-also"></a>Consulte também

- [Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

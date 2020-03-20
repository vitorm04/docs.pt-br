---
title: Relações e restrições de esquema XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150708"
---
# <a name="xml-schema-constraints-and-relationships"></a>Relações e restrições de esquema XML
Em um esquema de definição de Esquema XML (XSD), você pode especificar restrições (restrições únicas, chave e keyref) e relacionamentos (usando a anotação **msdata:Relacionamento).** Este tópico explica como as restrições e relacionamentos especificados em um <xref:System.Data.DataSet>Esquema XML são interpretados para gerar o .  
  
 Em geral, em um Esquema XML, você especifica a anotação **msdata:Relacionamento** se quiser gerar apenas relacionamentos no **Conjunto de Dados**. Para obter mais informações, consulte [Gerando relações de conjunto de dados a partir de XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md). Você especifica restrições (exclusivo, chave e keyref) se quiser gerar restrições no **Conjunto de Dados**. Observe que as restrições de chave e keyref também são usadas para gerar relacionamentos, como explicado posteriormente neste tópico.  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>Gerando um Relacionamento a partir de restrições de chave e keyref  
 Em vez de especificar a anotação **msdata:Relacionamento,** você pode especificar as restrições de teclas e keyref, que são usadas durante o processo de mapeamento do Esquema XML para gerar não apenas as restrições, mas também a relação no **Conjunto de Dados**. No entanto, `msdata:ConstraintOnly="true"` se você especificar no elemento **keyref,** o **DataSet** incluirá apenas as restrições e não incluirá o relacionamento.  
  
 O exemplo a seguir mostra um esquema XML que inclui elementos **de Ordem** e **OrderDetail,** que não estão aninhados. O esquema também especifica as restrições de chave e keyref.  
  
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
  
 O **Conjunto de Dados** gerado durante o processo de mapeamento do Esquema XML inclui as tabelas **Order** and **OrderDetail.** Além disso, o **DataSet** inclui relacionamentos e restrições. O exemplo a seguir mostra essas relações e restrições. Observe que o esquema não especifica a anotação **msdata:Relacionamento;** em vez disso, as restrições de chave e keyref são usadas para gerar a relação.  
  
```text
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
  
 No exemplo do esquema anterior, os elementos **Order** **e OrderDetail** não estão aninhados. No exemplo do esquema a seguir, esses elementos são aninhados. No entanto, nenhuma **anotação msdata:Relacionamento** é especificada; portanto, uma relação implícita é assumida. Para obter mais informações, consulte [Mapear relações implícitas entre elementos de esquema aninhados](map-implicit-relations-between-nested-schema-elements.md). O esquema também especifica as restrições de chave e keyref.  
  
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
  
 O **Conjunto de Dados** resultante do processo de mapeamento do Esquema XML inclui duas tabelas:  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 O **DataSet** também inclui os dois relacionamentos (um baseado no **msdata:anotação de relacionamento** e outro com base nas restrições de chave e keyref) e várias restrições. O exemplo a seguir mostra as relações e restrições.  
  
```text
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
  
 Se uma restrição keyref referente a uma tabela aninhada contiver a anotação **msdata:IsNested="true",** o **DataSet** criará uma única relação aninhada baseada na restrição keyref e na restrição única/chave relacionada.  
  
## <a name="see-also"></a>Confira também

- [Derivando a estrutura relacional do DataSet do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)

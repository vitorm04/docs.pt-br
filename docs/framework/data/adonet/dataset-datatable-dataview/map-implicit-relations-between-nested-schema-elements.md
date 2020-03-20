---
title: Mapear relações implícitas entre elementos de esquema aninhados
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150957"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapear relações implícitas entre elementos de esquema aninhados
Um esquema de definição de Esquema XML (XSD) pode ter tipos complexos aninhados dentro um do outro. Neste caso, o processo de mapeamento aplica o <xref:System.Data.DataSet>mapeamento padrão e cria o seguinte no :  
  
- Uma tabela para cada um dos tipos complexos (pai e filho).  
  
- Se não houver nenhuma restrição única no pai, uma coluna de chave principal adicional por definição de tabela chamada *TableName*_Id onde *TableName* é o nome da tabela pai.  
  
- Uma restrição de chave primária na tabela pai identificando a coluna adicional como a chave principal (definindo a propriedade **IsPrimaryKey** para **True**). A restrição é\# \# chamada Restrição onde é 1, 2, 3, e assim por diante. Por exemplo, o nome padrão da primeira restrição é Restrição1.  
  
- Uma restrição de chave estrangeira na tabela infantil identificando a coluna adicional como a chave estrangeira referente à chave primária da tabela-mãe. A restrição é nomeada *ParentTable_ChildTable* onde *ParentTable* é o nome da tabela dos pais e *ChildTable* é o nome da tabela filho.  
  
- Uma relação de dados entre as tabelas pai e filho.  
  
 O exemplo a seguir mostra um esquema onde **orderdetail** é um elemento filho da **Ordem**.  
  
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
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 O processo de mapeamento do Esquema XML cria o seguinte no **DataSet**:  
  
- Uma **ordem** e uma tabela **OrderDetail.**  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Uma restrição única na mesa **da Ordem.** Observe que a propriedade **IsPrimaryKey** está definida **como True**.  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- Uma restrição de chave estrangeira na tabela **OrderDetail.**  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- Uma relação entre as tabelas **Ordem** e **OrdemDetalhe.** A **propriedade Aninhado** para esta relação é definida como **True** porque os elementos **Order** e **OrderDetail** estão aninhados no esquema.  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>Confira também

- [Gerar relações de DataSet do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)

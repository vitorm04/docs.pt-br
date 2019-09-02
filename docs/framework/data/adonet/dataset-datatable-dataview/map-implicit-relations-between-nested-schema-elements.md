---
title: Mapear relações implícitas entre elementos de esquema aninhados
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: e9ea85db98a577991e06e0239a0738a2ca5bada6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203485"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapear relações implícitas entre elementos de esquema aninhados
Um esquema XSD (linguagem de definição de esquema XML) pode ter tipos complexos aninhados dentro um do outro. Nesse caso, o processo de mapeamento aplica o mapeamento padrão e cria o seguinte no <xref:System.Data.DataSet>:  
  
- Uma tabela para cada um dos tipos complexos (pai e filho).  
  
- Se não existir nenhuma restrição exclusiva no pai, uma coluna de chave primária adicional por definição de tabela denominada *TableName*_Id, em que *TableName* é o nome da tabela pai.  
  
- Uma restrição PRIMARY KEY na tabela pai que identifica a coluna adicional como a chave primária (definindo a propriedade **IsPrimaryKey** como **true**). A restrição é chamada de\# restrição \# , em que é 1, 2, 3 e assim por diante. Por exemplo, o nome padrão para a primeira restrição é Constraint1.  
  
- Uma restrição FOREIGN KEY na tabela filho que identifica a coluna adicional como a chave estrangeira que faz referência à chave primária da tabela pai. A restrição é denominada *ParentTable_ChildTable* , em que *ParentTable* é o nome da tabela pai e *ChildTable* é o nome da tabela filho.  
  
- Uma relação de dados entre as tabelas pai e filho.  
  
 O exemplo a seguir mostra um esquema em que **OrderDetail** é um elemento filho de **Order**.  
  
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
  
 O processo de mapeamento de esquema XML cria o seguinte no **conjunto de conjuntos**:  
  
- Uma **ordem** e uma tabela **OrderDetail** .  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- Uma restrição UNIQUE na tabela de **pedidos** . Observe que a Propriedade IsPrimaryKey está definida como **true**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- Uma restrição FOREIGN KEY na tabela **OrderDetail** .  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- Uma relação entre as tabelas **Order** e **OrderDetail** . A Propriedade aninhada para essa relação é definida como **true** porque os elementos **Order** e **OrderDetail** estão aninhados no esquema.  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Gerando relações de conjunto de dados do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

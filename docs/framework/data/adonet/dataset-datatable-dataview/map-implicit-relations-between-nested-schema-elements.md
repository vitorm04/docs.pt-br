---
title: Mapear relações implícita entre elementos de esquema aninhados
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 73cd8a83021934de3b8e3bf494a4f59dd32e183c
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493614"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapear relações implícita entre elementos de esquema aninhados
Um esquema XSD (linguagem) de definição de esquema XML pode ter tipos complexos aninhados dentro uma da outra. Nesse caso, o processo de mapeamento se aplica o mapeamento padrão e cria o seguinte no <xref:System.Data.DataSet>:  
  
-   Uma tabela para cada um dos tipos complexos (pai e filho).  
  
-   Não se existir nenhuma restrição exclusiva no pai, a coluna de chave primária adicional um acordo com a definição de tabela denominada *TableName*ID onde *TableName* é o nome da tabela pai.  
  
-   Uma restrição de chave primária na tabela pai que identifica a coluna adicional, como a chave primária (definindo o **IsPrimaryKey** propriedade **verdadeiro**). A restrição é denominada restrição\# onde \# é 1, 2, 3 e assim por diante. Por exemplo, o nome padrão para a primeira restrição é Constraint1.  
  
-   Uma restrição de chave estrangeira na tabela filho que identifica a coluna adicional, como a chave estrangeira referindo-se para a chave primária da tabela pai. A restrição é nomeada *ParentTable_ChildTable* onde *ParentTable* é o nome da tabela pai e *ChildTable* é o nome da tabela filho.  
  
-   Uma relação de dados entre as tabelas pai e filho.  
  
 O exemplo a seguir mostra um esquema no qual **OrderDetail** é um elemento filho do **ordem**.  
  
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
  
 O processo de mapeamento de esquema XML cria o seguinte a **conjunto de dados**:  
  
-   Uma **ordem** e uma **OrderDetail** tabela.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Uma restrição exclusiva na **ordem** tabela. Observe que o **IsPrimaryKey** estiver definida como **verdadeiro**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   Uma restrição de chave estrangeira na **OrderDetail** tabela.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   Uma relação entre o **ordem** e **OrderDetail** tabelas. O **Nested** propriedade para essa relação é definida como **verdadeiro** porque o **ordem** e **OrderDetail** elementos são aninhados no esquema .  
  
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
 [Gerando relações de conjunto de dados do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

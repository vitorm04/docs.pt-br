---
title: "Mapear relações implícita entre elementos de esquema aninhada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b3e3243384bd1dd55661a87ee67cc3052b94e923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Mapear relações implícita entre elementos de esquema aninhada
Um esquema de linguagem XSD de definição de esquema XML pode ter tipos complexos aninhados dentro de uma outra. Nesse caso, o processo de mapeamento aplica-se o mapeamento padrão e cria o seguinte o <xref:System.Data.DataSet>:  
  
-   Uma tabela para cada um dos tipos complexos (pai e filho).  
  
-   Não se existir nenhuma restrição exclusiva no pai, a coluna de chave primária adicional um por definição da tabela denominada *TableName*ID onde *TableName* é o nome da tabela pai.  
  
-   Uma restrição de chave primária na tabela pai que identifica a coluna adicional, como a chave primária (definindo o **IsPrimaryKey** propriedade **True**). A restrição é nomeada restrição *#*  onde  *#*  é 1, 2, 3 e assim por diante. Por exemplo, o nome padrão para a primeira restrição é Constraint1.  
  
-   Uma restrição de chave estrangeira na tabela filho que identifica a coluna adicional de chave estrangeira que faz referência à chave primária da tabela pai. A restrição é nomeada *ParentTable_ChildTable* onde *ParentTable* é o nome da tabela pai e *ChildTable* é o nome da tabela filho.  
  
-   Uma relação de dados entre as tabelas pai e filho.  
  
 O exemplo a seguir mostra um esquema onde **OrderDetail** é um elemento filho do **ordem**.  
  
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
  
 O processo de mapeamento de esquema XML cria o seguinte o **DataSet**:  
  
-   Um **ordem** e um **OrderDetail** tabela.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Uma restrição exclusiva no **ordem** tabela. Observe que o **IsPrimaryKey** está definida como **True**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   Uma restrição de chave estrangeira no **OrderDetail** tabela.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   Uma relação entre o **ordem** e **OrderDetail** tabelas. O **aninhadas** para essa relação é definida como **True** porque o **ordem** e **OrderDetail** elementos estão aninhados no esquema .  
  
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
 [Gerar relações de conjunto de dados de esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Restrições de esquema (XSD) de XML de mapeamento para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

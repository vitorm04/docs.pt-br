---
title: "Mapear keyref restrições de esquema XML (XSD) para restrições de conjunto de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f888a682510dbf768e5eab2ffdd530e2ac7cf635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapear keyref restrições de esquema XML (XSD) para restrições de conjunto de dados
O **keyref** elemento permite estabelecer links entre elementos dentro de um documento. Isso é semelhante a uma relação de chave estrangeira no banco de dados relacional. Se um esquema Especifica a **keyref** elemento, o elemento foi convertido durante o processo de mapeamento de esquema para uma restrição de chave estrangeira correspondente nas colunas nas tabelas do <xref:System.Data.DataSet>. Por padrão, o **keyref** elemento também gera uma relação com o **ParentTable**, **ChildTable**, **ParentColumn**e  **ChildColumn** propriedades especificadas na relação.  
  
 A tabela a seguir descreve o **msdata** atributos que você pode especificar o **keyref** elemento.  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|**MSDATA:ConstraintOnly**|Se **ConstraintOnly = "true"** é especificado no **keyref** elemento no esquema, uma restrição é criada, mas nenhuma relação é criada. Se esse atributo não for especificado (ou seja definido como **False**), a restrição e a relação são criados no **conjunto de dados**.|  
|**MSDATA:ConstraintName**|Se o **ConstraintName** atributo for especificado, seu valor é usado como o nome da restrição. Caso contrário, o **nome** atributo do **keyref** elemento no esquema fornece o nome da restrição no **conjunto de dados**.|  
|**MSDATA:UpdateRule**|Se o **UpdateRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído ao **UpdateRule** propriedade restrição no  **Conjunto de dados**. Caso contrário, o **UpdateRule** está definida como **Cascade**.|  
|**MSDATA:DeleteRule**|Se o **DeleteRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído ao **DeleteRule** propriedade restrição no  **Conjunto de dados**. Caso contrário, o **DeleteRule** está definida como **Cascade**.|  
|**MSDATA:AcceptRejectRule**|Se o **AcceptRejectRule** atributo é especificado no **keyref** elemento no esquema, seu valor é atribuído ao **AcceptRejectRule** propriedade restrição no  **Conjunto de dados**. Caso contrário, o **AcceptRejectRule** está definida como **nenhum**.|  
  
 O exemplo a seguir contém um esquema que especifica o **chave** e **keyref** relações entre o **OrderNumber** elemento filho do **ordem**  elemento e o **OrderNo** elemento filho do **OrderDetail** elemento.  
  
 No exemplo, o **OrderNumber** elemento filho do **OrderDetail** elemento refere-se ao **OrderNo** elemento chave filho do **ordem**elemento.  
  
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
  
 O processo de mapeamento XML Schema definition language (XSD) esquema produz os seguintes **DataSet** com duas tabelas:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Além disso, o **DataSet** define as seguintes restrições:  
  
-   Uma restrição exclusiva no **ordem** tabela.  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   Uma relação entre o **ordem** e **OrderDetail** tabelas. O **aninhadas** está definida como **False** porque os dois elementos não estão aninhados no esquema.  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   Uma restrição de chave estrangeira no **OrderDetail** tabela.  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Gerando relações de conjunto de dados do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

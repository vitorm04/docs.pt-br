---
title: Mapear restrições de esquema XML (XSD) keyref para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 611322065a4df53d1a3149ef4e1ca5592f149081
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203447"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapear restrições de esquema XML (XSD) keyref para restrições de DataSet
O elemento **keyref** permite que você estabeleça links entre elementos dentro de um documento. Isso é semelhante a uma relação de chave estrangeira em um banco de dados relacional. Se um esquema especificar o elemento **keyref** , o elemento será convertido durante o processo de mapeamento de esquema para uma restrição de chave estrangeira correspondente nas colunas nas tabelas do <xref:System.Data.DataSet>. Por padrão, o elemento **keyref** também gera uma relação, com as **Propriedades parentID**, **ChildTable**, **ParentColumn**e **ChildColumn** especificadas na relação.  
  
 A tabela a seguir descreve os atributos **MSDATA** que você pode especificar no elemento **keyref** .  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Se **ConstraintOnly = "true"** for especificado no elemento **keyref** no esquema, uma restrição será criada, mas nenhuma relação será criada. Se esse atributo não for especificado (ou estiver definido como **false**), a restrição e a relação serão criadas no **conjunto**de um.|  
|**msdata:ConstraintName**|Se o atributo ConstraintName for especificado, seu valor será usado como o nome da restrição. Caso contrário, o atributo **Name** do elemento **keyref** no esquema fornecerá o nome da restrição no **DataSet**.|  
|**msdata:UpdateRule**|Se o atributo **UpdateRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade de restrição **UpdateRule** no **conjunto**de valores. Caso contrário, a propriedade **UpdateRule** será definida como **Cascade**.|  
|**msdata:DeleteRule**|Se o atributo **DeleteRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade de restrição **DeleteRule** no **conjunto**de valores. Caso contrário, a propriedade **DeleteRule** será definida como **Cascade**.|  
|**msdata:AcceptRejectRule**|Se o atributo **AcceptRejectRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade de restrição **AcceptRejectRule** no **conjunto**de valores. Caso contrário, a propriedade **AcceptRejectRule** será definida como **None**.|  
  
 O exemplo a seguir contém um esquema que especifica as relações de **chave** e **keyref** entre o elemento filho **OrderNumber** do elemento **Order** e o elemento filho **orderno** de **OrderDetail** elementos.  
  
 No exemplo, o elemento filho **OrderNumber** do elemento **OrderDetail** refere-se ao elemento filho da chave **orderno** do elemento **Order** .  
  
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
  
 O processo de mapeamento de esquema XSD (linguagem de definição de esquema XML) produz o seguinte **conjunto** de um com duas tabelas:  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Além disso, o **conjunto** de os define as seguintes restrições:  
  
- Uma restrição UNIQUE na tabela de **pedidos** .  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Uma relação entre as tabelas **Order** e **OrderDetail** . A Propriedade aninhada está definida como **false** porque os dois elementos não estão aninhados no esquema.  
  
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
  
- Uma restrição FOREIGN KEY na tabela **OrderDetail** .  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>Consulte também

- [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Gerando relações de conjunto de dados do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

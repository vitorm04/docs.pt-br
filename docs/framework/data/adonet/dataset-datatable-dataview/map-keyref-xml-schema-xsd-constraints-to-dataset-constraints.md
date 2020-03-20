---
title: Mapear restrições de esquema XML (XSD) keyref para restrições de DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150877"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Mapear restrições de esquema XML (XSD) keyref para restrições de DataSet
O elemento **keyref** permite estabelecer links entre elementos dentro de um documento. Isso é semelhante a uma relação-chave estrangeira em um banco de dados relacional. Se um esquema especificar o elemento **keyref,** o elemento será convertido durante o processo de mapeamento do esquema <xref:System.Data.DataSet>para uma restrição de tecla estrangeira correspondente nas colunas nas tabelas do . Por padrão, o elemento **keyref** também gera uma relação com as propriedades **ParentTable**, **ChildTable,** **ParentColumn**e **ChildColumn** especificadas na relação.  
  
 A tabela a seguir descreve os **atributos msdata** que você pode especificar no elemento **keyref.**  
  
|Nome do atributo|Descrição|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|Se **ConstraintOnly="true"** for especificado no elemento **keyref** no esquema, uma restrição será criada, mas nenhuma relação será criada. Se esse atributo não for especificado (ou for definido como **Falso),** tanto a restrição quanto a relação serão criadas no **Conjunto de Dados**.|  
|**msdata:ConstraintName**|Se o atributo **ConstraintName** for especificado, seu valor será usado como o nome da restrição. Caso contrário, o atributo de **nome** do elemento **keyref** no esquema fornece o nome de restrição no **Conjunto de Dados**.|  
|**msdata:UpdateRule**|Se o atributo **UpdateRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade de restrição **UpdateRule** no **DataSet**. Caso contrário, a propriedade **UpdateRule** será definida **como Cascade**.|  
|**msdata:DeleteRule**|Se o atributo **DeleteRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade **DeleteRule** no **Conjunto de Dados**. Caso contrário, a propriedade **DeleteRule** será definida **como Cascade**.|  
|**msdata:AcceptRejectRule**|Se o atributo **AcceptRejectRule** for especificado no elemento **keyref** no esquema, seu valor será atribuído à propriedade **AcceptRejectRule** no **DataSet**. Caso contrário, a propriedade **AcceptRejectRule** será definida como **Nenhuma**.|  
  
 O exemplo a seguir contém um esquema que especifica as relações **de chave** e **keyref** entre o elemento **'OrderNumber** child' do elemento **Order's** e o elemento **OrderNo** child do elemento **OrderDetail.**  
  
 No exemplo, o elemento **'OrderNumber** child' do elemento **OrderDetail** refere-se ao elemento **'Ordem',** filho chave do elemento **Ordem.**  
  
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
  
 O processo de mapeamento do esquema XML Schema (XSD) produz o seguinte **DataSet** com duas tabelas:  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Além disso, o **DataSet** define as seguintes restrições:  
  
- Uma restrição única na mesa **da Ordem.**  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- Uma relação entre as tabelas **Ordem** e **OrdemDetalhe.** A **propriedade Aninhado** é definida como **False** porque os dois elementos não estão aninhados no esquema.  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- Uma restrição de chave estrangeira na tabela **OrderDetail.**  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a>Confira também

- [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Gerar relações de DataSet do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)

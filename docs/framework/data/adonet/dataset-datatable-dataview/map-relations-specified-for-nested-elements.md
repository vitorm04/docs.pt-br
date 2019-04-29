---
title: Mapear relações especificadas para elementos aninhados
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 9772f077991c758be65bbb44b9474f1ad341371f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785373"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapear relações especificadas para elementos aninhados
Um esquema pode incluir um **msdata:Relationship** anotação para especificar explicitamente o mapeamento entre dois elementos no esquema. Os dois elementos especificados em **msdata:Relationship** podem ser aninhadas no esquema, mas não precisa ser. Usa o processo de mapeamento **msdata:Relationship** no esquema para gerar a relação de chave estrangeira/chave primária entre as duas colunas.  
  
 O exemplo a seguir mostra um esquema XML no qual o **OrderDetail** é um elemento filho do **ordem**. O **msdata:Relationship** identifica essa relação de pai-filho e especifica que o **OrderNumber** coluna resultantes **ordem** tabela está relacionada com o **OrderNo** coluna resultantes **OrderDetail** tabela.  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"   
                                msdata:parent="Order"   
                                msdata:child="OrderDetail"   
                                msdata:parentkey="OrderNumber"   
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 O processo de mapeamento de esquema XML cria o seguinte no <xref:System.Data.DataSet>:  
  
- Uma **ordem** e uma **OrderDetail** tabela.  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Uma relação entre o **ordem** e **OrderDetail** tabelas. O **Nested** propriedade para essa relação é definida como **verdadeiro** porque o **ordem** e **OrderDetail** elementos são aninhados no esquema .  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 O processo de mapeamento não cria todas as restrições.  
  
## <a name="see-also"></a>Consulte também

- [Gerando relações de conjunto de dados do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

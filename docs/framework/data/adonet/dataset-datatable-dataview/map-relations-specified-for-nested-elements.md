---
title: Mapear relações especificadas para elementos aninhados
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150890"
---
# <a name="map-relations-specified-for-nested-elements"></a>Mapear relações especificadas para elementos aninhados
Um esquema pode incluir uma anotação **msdata:Relacionamento** para especificar explicitamente o mapeamento entre quaisquer dois elementos no esquema. Os dois elementos especificados em **msdata:Relacionamento** podem ser aninhados no esquema, mas não precisa ser. O processo de mapeamento usa **msdata:Relationship** in the schema para gerar a relação chave principal/estrangeira entre as duas colunas.  
  
 O exemplo a seguir mostra um esquema XML no qual o elemento **OrderDetail** é um elemento filho da **Ordem**. O **msdata:Relationship** identifica essa relação pai-filho e especifica que a coluna **OrderNumber** da tabela Order resultante **está** relacionada à coluna **OrderNo** da tabela **OrderDetail** resultante.  
  
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
  
 O processo de mapeamento do Esquema XML cria o seguinte no: <xref:System.Data.DataSet>  
  
- Uma **ordem** e uma tabela **OrderDetail.**  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- Uma relação entre as tabelas **Ordem** e **OrdemDetalhe.** A **propriedade Aninhado** para esta relação é definida como **True** porque os elementos **Order** e **OrderDetail** estão aninhados no esquema.  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 O processo de mapeamento não cria nenhuma restrição.  
  
## <a name="see-also"></a>Confira também

- [Gerar relações de DataSet do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)

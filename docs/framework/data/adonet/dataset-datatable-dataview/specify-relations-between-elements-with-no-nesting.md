---
title: Especificar relações entre elementos sem nenhum aninhamento
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: bee427c6cdf76792773ea827c8772b276ff29c31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150812"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a>Especificar relações entre elementos sem nenhum aninhamento
Quando os elementos não estão aninhados, nenhuma relação implícita é criada. No entanto, você pode especificar explicitamente as relações entre elementos que não estão aninhados usando a anotação **msdata:Relacionamento.**  
  
 O exemplo a seguir mostra um esquema XML no qual a anotação **msdata:Relationship** é especificada entre os elementos **Ordem** e **OrderDetail,** que não estão aninhados. A anotação **msdata:Relacionamento** é especificada como o elemento filho do elemento **Esquema.**  
  
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
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"
                            msdata:child="OrderDetail"
                            msdata:parentkey="OrderNumber"
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 O processo de mapeamento de esquema xml schema (XSD) cria uma <xref:System.Data.DataSet> tabela com tabelas **Order** and **OrderDetail** e uma relação especificada entre essas duas tabelas, conforme mostrado abaixo.  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a>Confira também

- [Gerar relações de DataSet do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)

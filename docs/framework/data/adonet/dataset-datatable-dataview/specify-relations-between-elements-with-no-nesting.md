---
title: Especificar relações entre elementos sem nenhum aninhamento
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 83dce7173c016a7d7d2d626bb7a3606de29d54ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204472"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a>Especificar relações entre elementos sem nenhum aninhamento
Quando os elementos não são aninhados, nenhuma relação implícita é criada. No entanto, você pode especificar explicitamente as relações entre os elementos que não são aninhados usando a anotação **MSDATA: relationship** .  
  
 O exemplo a seguir mostra um esquema XML no qual a anotação **MSDATA: relationship** é especificada entre os elementos **Order** e **OrderDetail** , que não estão aninhados. A anotação **MSDATA: relationship** é especificada como o elemento filho do elemento **Schema** .  
  
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
  
 O processo de mapeamento de esquema XSD (linguagem de definição de esquema <xref:System.Data.DataSet> XML) cria um com tabelas **Order** e **OrderDetail** e uma relação especificada entre essas duas tabelas, como mostrado abaixo.  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a>Consulte também

- [Gerando relações de conjunto de dados do esquema XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md)
- [Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)

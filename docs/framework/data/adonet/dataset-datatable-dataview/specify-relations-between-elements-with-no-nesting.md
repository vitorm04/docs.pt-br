---
title: Especificar as relações entre os elementos com nenhuma aninhamento
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 1d178287150dfca4c379cf6e934370434c3cfc98
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760083"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="f5f14-102">Especificar as relações entre os elementos com nenhuma aninhamento</span><span class="sxs-lookup"><span data-stu-id="f5f14-102">Specify Relations Between Elements with No Nesting</span></span>
<span data-ttu-id="f5f14-103">Quando elementos não estão aninhados, nenhuma relação implícita é criadas.</span><span class="sxs-lookup"><span data-stu-id="f5f14-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="f5f14-104">No entanto, você pode especificar explicitamente relações entre os elementos que não estão aninhadas usando a **msdata:Relationship** anotação.</span><span class="sxs-lookup"><span data-stu-id="f5f14-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="f5f14-105">O exemplo a seguir mostra um esquema XML no qual o **msdata:Relationship** anotação é especificada entre a **ordem** e **OrderDetail** elementos, que não são aninhados.</span><span class="sxs-lookup"><span data-stu-id="f5f14-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="f5f14-106">O **msdata:Relationship** anotação é especificada como o elemento filho de **esquema** elemento.</span><span class="sxs-lookup"><span data-stu-id="f5f14-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="f5f14-107">O processo de mapeamento de esquema do esquema XML definition language (XSD) cria um <xref:System.Data.DataSet> com **ordem** e **OrderDetail** tabelas e uma relação especificada entre essas duas tabelas, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="f5f14-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber   
ChildTable: OrderDetail  
ChildColumns: OrderNo   
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5f14-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5f14-108">See Also</span></span>  
 [<span data-ttu-id="f5f14-109">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="f5f14-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="f5f14-110">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="f5f14-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="f5f14-111">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f5f14-111">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

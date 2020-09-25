---
title: Especificar relações entre elementos sem nenhum aninhamento
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 6684e992242d5c695f3c237f70de61b4dae1c48f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183397"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="ec1bf-102">Especificar relações entre elementos sem nenhum aninhamento</span><span class="sxs-lookup"><span data-stu-id="ec1bf-102">Specify Relations Between Elements with No Nesting</span></span>

<span data-ttu-id="ec1bf-103">Quando os elementos não são aninhados, nenhuma relação implícita é criada.</span><span class="sxs-lookup"><span data-stu-id="ec1bf-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="ec1bf-104">No entanto, você pode especificar explicitamente as relações entre os elementos que não são aninhados usando a anotação **MSDATA: relationship** .</span><span class="sxs-lookup"><span data-stu-id="ec1bf-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="ec1bf-105">O exemplo a seguir mostra um esquema XML no qual a anotação **MSDATA: relationship** é especificada entre os elementos **Order** e **OrderDetail** , que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="ec1bf-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="ec1bf-106">A anotação **MSDATA: relationship** é especificada como o elemento filho do elemento **Schema** .</span><span class="sxs-lookup"><span data-stu-id="ec1bf-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
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
  
 <span data-ttu-id="ec1bf-107">O processo de mapeamento de esquema XSD (linguagem de definição de esquema XML) cria um <xref:System.Data.DataSet> com tabelas **Order** e **OrderDetail** e uma relação especificada entre essas duas tabelas, como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="ec1bf-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec1bf-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="ec1bf-108">See also</span></span>

- [<span data-ttu-id="ec1bf-109">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ec1bf-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="ec1bf-110">Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="ec1bf-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="ec1bf-111">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ec1bf-111">ADO.NET Overview</span></span>](../ado-net-overview.md)

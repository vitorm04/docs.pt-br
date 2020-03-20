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
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="2df8f-102">Mapear relações especificadas para elementos aninhados</span><span class="sxs-lookup"><span data-stu-id="2df8f-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="2df8f-103">Um esquema pode incluir uma anotação **msdata:Relacionamento** para especificar explicitamente o mapeamento entre quaisquer dois elementos no esquema.</span><span class="sxs-lookup"><span data-stu-id="2df8f-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="2df8f-104">Os dois elementos especificados em **msdata:Relacionamento** podem ser aninhados no esquema, mas não precisa ser.</span><span class="sxs-lookup"><span data-stu-id="2df8f-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="2df8f-105">O processo de mapeamento usa **msdata:Relationship** in the schema para gerar a relação chave principal/estrangeira entre as duas colunas.</span><span class="sxs-lookup"><span data-stu-id="2df8f-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="2df8f-106">O exemplo a seguir mostra um esquema XML no qual o elemento **OrderDetail** é um elemento filho da **Ordem**.</span><span class="sxs-lookup"><span data-stu-id="2df8f-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="2df8f-107">O **msdata:Relationship** identifica essa relação pai-filho e especifica que a coluna **OrderNumber** da tabela Order resultante **está** relacionada à coluna **OrderNo** da tabela **OrderDetail** resultante.</span><span class="sxs-lookup"><span data-stu-id="2df8f-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="2df8f-108">O processo de mapeamento do Esquema XML cria o seguinte no: <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="2df8f-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="2df8f-109">Uma **ordem** e uma tabela **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="2df8f-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="2df8f-110">Uma relação entre as tabelas **Ordem** e **OrdemDetalhe.**</span><span class="sxs-lookup"><span data-stu-id="2df8f-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="2df8f-111">A **propriedade Aninhado** para esta relação é definida como **True** porque os elementos **Order** e **OrderDetail** estão aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="2df8f-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="2df8f-112">O processo de mapeamento não cria nenhuma restrição.</span><span class="sxs-lookup"><span data-stu-id="2df8f-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df8f-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="2df8f-113">See also</span></span>

- [<span data-ttu-id="2df8f-114">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="2df8f-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="2df8f-115">Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="2df8f-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="2df8f-116">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2df8f-116">ADO.NET Overview</span></span>](../ado-net-overview.md)

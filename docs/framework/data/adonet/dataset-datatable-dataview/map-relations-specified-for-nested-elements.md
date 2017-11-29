---
title: "Mapear relações definidas para elementos aninhados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9866b556f2ba09cef7616fea4a2a6d8135e6b8e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="580c9-102">Mapear relações definidas para elementos aninhados</span><span class="sxs-lookup"><span data-stu-id="580c9-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="580c9-103">Um esquema pode incluir um **msdata:Relationship** anotação para especificar explicitamente o mapeamento entre quaisquer dois elementos no esquema.</span><span class="sxs-lookup"><span data-stu-id="580c9-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="580c9-104">Os dois elementos especificados na **msdata:Relationship** podem ser aninhados no esquema, mas não precisa ser.</span><span class="sxs-lookup"><span data-stu-id="580c9-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="580c9-105">O processo de mapeamento usa **msdata:Relationship** no esquema para gerar a primária/chave relação de chave estrangeira entre as duas colunas.</span><span class="sxs-lookup"><span data-stu-id="580c9-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="580c9-106">O exemplo a seguir mostra um esquema XML no qual o **OrderDetail** é um elemento filho do **ordem**.</span><span class="sxs-lookup"><span data-stu-id="580c9-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="580c9-107">O **msdata:Relationship** identifica essa relação pai-filho e especifica que o **OrderNumber** coluna resultante **ordem** tabela está relacionada com o **OrderNo** coluna resultante **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="580c9-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="580c9-108">O processo de mapeamento de esquema XML cria o seguinte o <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="580c9-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="580c9-109">Um **ordem** e um **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="580c9-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="580c9-110">Uma relação entre o **ordem** e **OrderDetail** tabelas.</span><span class="sxs-lookup"><span data-stu-id="580c9-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="580c9-111">O **aninhadas** para essa relação é definida como **True** porque o **ordem** e **OrderDetail** elementos estão aninhados no esquema .</span><span class="sxs-lookup"><span data-stu-id="580c9-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="580c9-112">O processo de mapeamento não cria quaisquer restrições.</span><span class="sxs-lookup"><span data-stu-id="580c9-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="580c9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="580c9-113">See Also</span></span>  
 [<span data-ttu-id="580c9-114">Gerar relações de conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="580c9-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="580c9-115">Restrições de esquema (XSD) de XML de mapeamento para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="580c9-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="580c9-116">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="580c9-116">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

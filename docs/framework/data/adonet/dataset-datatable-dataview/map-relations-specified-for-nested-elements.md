---
title: Mapear relações especificadas para elementos aninhados
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 510a5e676df7bac274c6086b94e9a23e7540da20
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204640"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="8c3ff-102">Mapear relações especificadas para elementos aninhados</span><span class="sxs-lookup"><span data-stu-id="8c3ff-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="8c3ff-103">Um esquema pode incluir uma anotação **MSDATA: relationship** para especificar explicitamente o mapeamento entre quaisquer dois elementos no esquema.</span><span class="sxs-lookup"><span data-stu-id="8c3ff-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="8c3ff-104">Os dois elementos especificados em **MSDATA: relationship** podem ser aninhados no esquema, mas não precisam ser.</span><span class="sxs-lookup"><span data-stu-id="8c3ff-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="8c3ff-105">O processo de mapeamento usa a **relação MSDATA:** no esquema para gerar a relação de chave primária/chave estrangeira entre as duas colunas.</span><span class="sxs-lookup"><span data-stu-id="8c3ff-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="8c3ff-106">O exemplo a seguir mostra um esquema XML no qual o elemento **OrderDetail** é um elemento filho de **Order**.</span><span class="sxs-lookup"><span data-stu-id="8c3ff-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="8c3ff-107">A **relação MSDATA:** identifica essa relação pai-filho e especifica que a coluna **OrderNumber** da tabela de **ordem** resultante está relacionada à coluna **orderno** da tabela **OrderDetail** resultante.</span><span class="sxs-lookup"><span data-stu-id="8c3ff-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="8c3ff-108">O processo de mapeamento de esquema XML cria o seguinte <xref:System.Data.DataSet>no:</span><span class="sxs-lookup"><span data-stu-id="8c3ff-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="8c3ff-109">Uma **ordem** e uma tabela **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="8c3ff-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="8c3ff-110">Uma relação entre as tabelas **Order** e **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="8c3ff-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="8c3ff-111">A Propriedade aninhada para essa relação é definida como **true** porque os elementos **Order** e **OrderDetail** estão aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="8c3ff-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="8c3ff-112">O processo de mapeamento não cria nenhuma restrição.</span><span class="sxs-lookup"><span data-stu-id="8c3ff-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3ff-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c3ff-113">See also</span></span>

- [<span data-ttu-id="8c3ff-114">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="8c3ff-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="8c3ff-115">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="8c3ff-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- <span data-ttu-id="8c3ff-116">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8c3ff-116">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

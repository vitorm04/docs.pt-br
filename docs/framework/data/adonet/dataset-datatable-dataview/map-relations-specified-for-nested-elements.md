---
title: Mapear relações definidas para elementos aninhados
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 0346ba04fd8af6b5abc81fe994dd40f9a6a37c1d
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332462"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="f34ed-102">Mapear relações definidas para elementos aninhados</span><span class="sxs-lookup"><span data-stu-id="f34ed-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="f34ed-103">Um esquema pode incluir um **msdata:Relationship** anotação para especificar explicitamente o mapeamento entre dois elementos no esquema.</span><span class="sxs-lookup"><span data-stu-id="f34ed-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="f34ed-104">Os dois elementos especificados em **msdata:Relationship** podem ser aninhadas no esquema, mas não precisa ser.</span><span class="sxs-lookup"><span data-stu-id="f34ed-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="f34ed-105">Usa o processo de mapeamento **msdata:Relationship** no esquema para gerar a relação de chave estrangeira/chave primária entre as duas colunas.</span><span class="sxs-lookup"><span data-stu-id="f34ed-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="f34ed-106">O exemplo a seguir mostra um esquema XML no qual o **OrderDetail** é um elemento filho do **ordem**.</span><span class="sxs-lookup"><span data-stu-id="f34ed-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="f34ed-107">O **msdata:Relationship** identifica essa relação de pai-filho e especifica que o **OrderNumber** coluna resultantes **ordem** tabela está relacionada com o **OrderNo** coluna resultantes **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="f34ed-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="f34ed-108">O processo de mapeamento de esquema XML cria o seguinte no <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="f34ed-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="f34ed-109">Uma **ordem** e uma **OrderDetail** tabela.</span><span class="sxs-lookup"><span data-stu-id="f34ed-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="f34ed-110">Uma relação entre o **ordem** e **OrderDetail** tabelas.</span><span class="sxs-lookup"><span data-stu-id="f34ed-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="f34ed-111">O **Nested** propriedade para essa relação é definida como **verdadeiro** porque o **ordem** e **OrderDetail** elementos são aninhados no esquema .</span><span class="sxs-lookup"><span data-stu-id="f34ed-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="f34ed-112">O processo de mapeamento não cria todas as restrições.</span><span class="sxs-lookup"><span data-stu-id="f34ed-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34ed-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f34ed-113">See Also</span></span>  
 [<span data-ttu-id="f34ed-114">Gerando relações de conjunto de dados do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="f34ed-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="f34ed-115">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="f34ed-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="f34ed-116">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f34ed-116">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

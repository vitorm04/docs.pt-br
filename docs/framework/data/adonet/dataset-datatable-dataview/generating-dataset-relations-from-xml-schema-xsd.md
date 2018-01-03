---
title: "Gerar relações de conjunto de dados de esquema XML (XSD)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 916b9ad24c2ae2334635760a520116b4c19df314
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="aa207-102">Gerar relações de conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="aa207-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="aa207-103">Em um <xref:System.Data.DataSet>, formam uma associação entre duas ou mais colunas, criando uma relação pai-filho.</span><span class="sxs-lookup"><span data-stu-id="aa207-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="aa207-104">Há três maneiras para representar um **DataSet** relação dentro de um esquema de linguagem XSD de definição de esquema XML:</span><span class="sxs-lookup"><span data-stu-id="aa207-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="aa207-105">Especifica tipos complexos aninhados.</span><span class="sxs-lookup"><span data-stu-id="aa207-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="aa207-106">Use o **msdata:Relationship** anotação.</span><span class="sxs-lookup"><span data-stu-id="aa207-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="aa207-107">Especifique um **xs:keyref** sem o **msdata:ConstraintOnly** anotação.</span><span class="sxs-lookup"><span data-stu-id="aa207-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="aa207-108">Tipos complexos aninhados</span><span class="sxs-lookup"><span data-stu-id="aa207-108">Nested Complex Types</span></span>  
 <span data-ttu-id="aa207-109">Definições de tipo complexa aninhada em um esquema indicam as relações pai-filho dos elementos.</span><span class="sxs-lookup"><span data-stu-id="aa207-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="aa207-110">O fragmento de esquema XML a seguir mostra que **OrderDetail** é um elemento filho do **ordem** elemento.</span><span class="sxs-lookup"><span data-stu-id="aa207-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="aa207-111">O processo de mapeamento de esquema XML cria tabelas de **conjunto de dados** que correspondem aos tipos aninhados complexos no esquema.</span><span class="sxs-lookup"><span data-stu-id="aa207-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="aa207-112">Ele também cria colunas adicionais que são usadas como pai**-**colunas-filho para as tabelas geradas.</span><span class="sxs-lookup"><span data-stu-id="aa207-112">It also creates additional columns that are used as parent**-**child columns for the generated tables.</span></span> <span data-ttu-id="aa207-113">Observe que essas pai**-**colunas filho especificam relações, que não é o mesmo que especificar restrições de chave estrangeira/de chave primária.</span><span class="sxs-lookup"><span data-stu-id="aa207-113">Note that these parent**-**child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="aa207-114">MSDATA:Relationship anotação</span><span class="sxs-lookup"><span data-stu-id="aa207-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="aa207-115">O **msdata:Relationship** anotação permite que você especifique explicitamente as relações pai-filho entre elementos do esquema que não estão aninhadas.</span><span class="sxs-lookup"><span data-stu-id="aa207-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="aa207-116">O exemplo a seguir mostra a estrutura do **relação** elemento.</span><span class="sxs-lookup"><span data-stu-id="aa207-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="aa207-117">Os atributos do **msdata:Relationship** anotação identificar os elementos envolvidos na relação pai-filho, bem como o **parentkey** e **childkey** elementos e atributos envolvidos na relação.</span><span class="sxs-lookup"><span data-stu-id="aa207-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="aa207-118">O processo de mapeamento usa essas informações para gerar tabelas de **DataSet** e criar a relação chave primária/estrangeira chave entre essas tabelas.</span><span class="sxs-lookup"><span data-stu-id="aa207-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="aa207-119">Por exemplo, o fragmento de esquema a seguir especifica **ordem** e **OrderDetail** elementos no mesmo nível (não aninhados).</span><span class="sxs-lookup"><span data-stu-id="aa207-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="aa207-120">O esquema especifica um **msdata:Relationship** anotação, que especifica a relação pai-filho entre esses dois elementos.</span><span class="sxs-lookup"><span data-stu-id="aa207-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="aa207-121">Nesse caso, uma relação explicit deve ser especificada usando o **msdata:Relationship** anotação.</span><span class="sxs-lookup"><span data-stu-id="aa207-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="aa207-122">Usa o processo de mapeamento de **relação** elemento para criar uma relação pai-filho entre o **OrderNumber** coluna o **ordem** tabela e o **OrderNo** coluna o **OrderDetail** tabela o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="aa207-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="aa207-123">O processo de mapeamento especifica apenas a relação; ele não especificar automaticamente quaisquer restrições nos valores nessas colunas, assim como as restrições de chave key/foreign primárias em bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="aa207-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="aa207-124">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="aa207-124">In This Section</span></span>  
 [<span data-ttu-id="aa207-125">Mapear relações implícita entre elementos de esquema aninhados</span><span class="sxs-lookup"><span data-stu-id="aa207-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="aa207-126">Descreve as restrições e relações são criadas implicitamente em um **DataSet** quando elementos aninhados são encontrados no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="aa207-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="aa207-127">Mapear relações definidas para elementos aninhados</span><span class="sxs-lookup"><span data-stu-id="aa207-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="aa207-128">Descreve como definir explicitamente as relações em um **DataSet** para elementos aninhados no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="aa207-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="aa207-129">Especificar as relações entre os elementos sem nenhum aninhamento</span><span class="sxs-lookup"><span data-stu-id="aa207-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="aa207-130">Descreve como criar relações em um **DataSet** entre elementos de esquema XML que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="aa207-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="aa207-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="aa207-131">Related Sections</span></span>  
 [<span data-ttu-id="aa207-132">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="aa207-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="aa207-133">Descreve a estrutura relacional, ou o esquema, de um **conjunto de dados** que é criado a partir do esquema de linguagem XSD de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="aa207-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="aa207-134">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="aa207-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="aa207-135">Descreve os elementos de esquema XML usados para criar restrições de chave estrangeiras e exclusivas em uma **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="aa207-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa207-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa207-136">See Also</span></span>  
 <span data-ttu-id="aa207-137">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="aa207-137">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

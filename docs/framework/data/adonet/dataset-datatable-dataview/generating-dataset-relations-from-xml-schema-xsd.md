---
title: Gerar relações de DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: d00f07ee3338941b7de1bb890f71cd3c2d120246
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784651"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="534c9-102">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="534c9-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="534c9-103">Em um <xref:System.Data.DataSet>, você formam uma associação entre duas ou mais colunas criando uma relação pai-filho.</span><span class="sxs-lookup"><span data-stu-id="534c9-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="534c9-104">Há três maneiras de representar uma relação de conjunto de um **DataSet** em um esquema XSD (linguagem de definição de esquema XML):</span><span class="sxs-lookup"><span data-stu-id="534c9-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="534c9-105">Especifique tipos complexos aninhados.</span><span class="sxs-lookup"><span data-stu-id="534c9-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="534c9-106">Use a anotação **MSDATA: relationship** .</span><span class="sxs-lookup"><span data-stu-id="534c9-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="534c9-107">Especifique um **xs: keyref** sem a anotação **MSDATA: ConstraintOnly** .</span><span class="sxs-lookup"><span data-stu-id="534c9-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="534c9-108">Tipos complexos aninhados</span><span class="sxs-lookup"><span data-stu-id="534c9-108">Nested Complex Types</span></span>  
 <span data-ttu-id="534c9-109">Definições de tipo complexo aninhadas em um esquema indicam as relações pai-filho dos elementos.</span><span class="sxs-lookup"><span data-stu-id="534c9-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="534c9-110">O fragmento de esquema XML a seguir mostra que **OrderDetail** é um elemento filho do elemento **Order** .</span><span class="sxs-lookup"><span data-stu-id="534c9-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="534c9-111">O processo de mapeamento de esquema XML cria tabelas no **conjunto** de um que correspondem aos tipos complexos aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="534c9-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="534c9-112">Ele também cria colunas adicionais que são usadas como colunas **-** filho pai para as tabelas geradas.</span><span class="sxs-lookup"><span data-stu-id="534c9-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="534c9-113">Observe que essas colunas **-** filho pai especificam relações, que não são as mesmas que especificar restrições de chave primária/Foreign Key.</span><span class="sxs-lookup"><span data-stu-id="534c9-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="534c9-114">MSDATA: anotação de relação</span><span class="sxs-lookup"><span data-stu-id="534c9-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="534c9-115">A anotação **MSDATA: relationship** permite especificar explicitamente as relações pai-filho entre os elementos no esquema que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="534c9-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="534c9-116">O exemplo a seguir mostra a estrutura do elemento **relationship** .</span><span class="sxs-lookup"><span data-stu-id="534c9-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="534c9-117">Os atributos da anotação **MSDATA: relationship** identificam os elementos envolvidos na relação pai-filho, bem como os elementos e atributos **ParentKey** e **ChildKey** envolvidos na relação.</span><span class="sxs-lookup"><span data-stu-id="534c9-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="534c9-118">O processo de mapeamento usa essas informações para gerar tabelas no **conjunto** de dados e para criar a relação de chave primária/chave estrangeira entre essas tabelas.</span><span class="sxs-lookup"><span data-stu-id="534c9-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="534c9-119">Por exemplo, o seguinte fragmento de esquema especifica os elementos **Order** e **OrderDetail** no mesmo nível (não aninhado).</span><span class="sxs-lookup"><span data-stu-id="534c9-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="534c9-120">O esquema especifica uma anotação **MSDATA: relationship** , que especifica a relação pai-filho entre esses dois elementos.</span><span class="sxs-lookup"><span data-stu-id="534c9-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="534c9-121">Nesse caso, uma relação explícita deve ser especificada usando a anotação **MSDATA: relationship** .</span><span class="sxs-lookup"><span data-stu-id="534c9-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="534c9-122">O processo de mapeamento usa o elemento **relationship** para criar uma relação pai-filho entre a coluna **OrderNumber** na tabela **Order** e a coluna **orderno** na tabela **OrderDetail** no **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="534c9-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="534c9-123">O processo de mapeamento especifica apenas a relação; Ele não especifica automaticamente nenhuma restrição nos valores dessas colunas, assim como as restrições de chave primária/chave estrangeira em bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="534c9-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="534c9-124">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="534c9-124">In This Section</span></span>  
 [<span data-ttu-id="534c9-125">Mapear relações implícita entre elementos de esquema aninhados</span><span class="sxs-lookup"><span data-stu-id="534c9-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="534c9-126">Descreve as restrições e relações criadas implicitamente em um conjunto de um **DataSet** quando elementos aninhados são encontrados no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="534c9-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="534c9-127">Mapear relações definidas para elementos aninhados</span><span class="sxs-lookup"><span data-stu-id="534c9-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="534c9-128">Descreve como definir explicitamente relações em um **DataSet** para elementos aninhados no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="534c9-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="534c9-129">Especificar as relações entre os elementos sem nenhum aninhamento</span><span class="sxs-lookup"><span data-stu-id="534c9-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="534c9-130">Descreve como criar relações em um conjunto de um **DataSet** entre elementos de esquema XML que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="534c9-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="534c9-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="534c9-131">Related Sections</span></span>  
 [<span data-ttu-id="534c9-132">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="534c9-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="534c9-133">Descreve a estrutura relacional, ou esquema, de um **conjunto** de dados criado a partir do esquema XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="534c9-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="534c9-134">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="534c9-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="534c9-135">Descreve os elementos de esquema XML usados para criar restrições de chave estrangeira e exclusivas em um **conjunto**de uma.</span><span class="sxs-lookup"><span data-stu-id="534c9-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534c9-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="534c9-136">See also</span></span>

- <span data-ttu-id="534c9-137">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="534c9-137">[ADO.NET Overview](../ado-net-overview.md)</span></span>

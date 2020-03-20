---
title: Gerar relações de DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151124"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="a7435-102">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="a7435-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="a7435-103">Em <xref:System.Data.DataSet>um , você forma uma associação entre duas ou mais colunas criando uma relação pai-filho.</span><span class="sxs-lookup"><span data-stu-id="a7435-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="a7435-104">Existem três maneiras de representar uma relação **DataSet** dentro de um esquema de definição de Esquema XML (XSD):</span><span class="sxs-lookup"><span data-stu-id="a7435-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="a7435-105">Especifique tipos complexos aninhados.</span><span class="sxs-lookup"><span data-stu-id="a7435-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="a7435-106">Use a anotação **msdata:Relacionamento.**</span><span class="sxs-lookup"><span data-stu-id="a7435-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="a7435-107">Especifique um **xs:keyref** sem a anotação **msdata:ConstraintOnly.**</span><span class="sxs-lookup"><span data-stu-id="a7435-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="a7435-108">Tipos complexos aninhados</span><span class="sxs-lookup"><span data-stu-id="a7435-108">Nested Complex Types</span></span>  
 <span data-ttu-id="a7435-109">Definições complexas de tipo aninhadas em um esquema indicam as relações pai-filho dos elementos.</span><span class="sxs-lookup"><span data-stu-id="a7435-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="a7435-110">O fragmento de Esquema XML a seguir mostra que **OrderDetail** é um elemento filho do elemento **Ordem.**</span><span class="sxs-lookup"><span data-stu-id="a7435-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="a7435-111">O processo de mapeamento xml schema cria tabelas no **Conjunto de Dados** que correspondem aos tipos complexos aninhados no esquema.</span><span class="sxs-lookup"><span data-stu-id="a7435-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="a7435-112">Ele também cria colunas adicionais**-** que são usadas como colunas de filhos-mãe para as tabelas geradas.</span><span class="sxs-lookup"><span data-stu-id="a7435-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="a7435-113">Observe que**-** essas colunas filho-mãe especificam relacionamentos, o que não é o mesmo que especificar as restrições de chave primária/estrangeira.</span><span class="sxs-lookup"><span data-stu-id="a7435-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="a7435-114">msdata:Anotação de relacionamento</span><span class="sxs-lookup"><span data-stu-id="a7435-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="a7435-115">A anotação **msdata:Relacionamento** permite especificar explicitamente as relações pai-filho entre elementos no esquema que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="a7435-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="a7435-116">O exemplo a seguir mostra a estrutura do elemento **Relacionamento.**</span><span class="sxs-lookup"><span data-stu-id="a7435-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="a7435-117">Os atributos da anotação **msdata:Relacionamento** identificam os elementos envolvidos na relação pai-filho, bem como os elementos e atributos de **chave parental** e **infantil** envolvidos na relação.</span><span class="sxs-lookup"><span data-stu-id="a7435-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="a7435-118">O processo de mapeamento usa essas informações para gerar tabelas no **DataSet** e para criar a relação chave principal/estrangeira entre essas tabelas.</span><span class="sxs-lookup"><span data-stu-id="a7435-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="a7435-119">Por exemplo, o fragmento de esquema a seguir especifica elementos **de Ordem** e **OrderDetail** no mesmo nível (não aninhado).</span><span class="sxs-lookup"><span data-stu-id="a7435-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="a7435-120">O esquema especifica uma **anotação msdata:Relacionamento,** que especifica a relação pai-filho entre esses dois elementos.</span><span class="sxs-lookup"><span data-stu-id="a7435-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="a7435-121">Neste caso, uma relação explícita deve ser especificada usando a anotação **msdata:Relacionamento.**</span><span class="sxs-lookup"><span data-stu-id="a7435-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="a7435-122">O processo de mapeamento usa o elemento **Relacionamento** para criar uma relação pai-filho entre a coluna **OrderNumber** na tabela **Order** e a coluna **OrderNo** na tabela **OrderDetail** no **Conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="a7435-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="a7435-123">O processo de mapeamento especifica apenas a relação; não especifica automaticamente quaisquer restrições sobre os valores nessas colunas, assim como as restrições de chave primária/estrangeira nas bases de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="a7435-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="a7435-124">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a7435-124">In This Section</span></span>  
 [<span data-ttu-id="a7435-125">Mapear relações implícitas entre elementos de esquema aninhados</span><span class="sxs-lookup"><span data-stu-id="a7435-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="a7435-126">Descreve as restrições e relações que são implicitamente criadas em um **DataSet** quando elementos aninhados são encontrados no Esquema XML.</span><span class="sxs-lookup"><span data-stu-id="a7435-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="a7435-127">Mapear relações especificadas para elementos aninhados</span><span class="sxs-lookup"><span data-stu-id="a7435-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="a7435-128">Descreve como definir explicitamente as relações em um **DataSet** para elementos aninhados no Esquema XML.</span><span class="sxs-lookup"><span data-stu-id="a7435-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="a7435-129">Especificar relações entre elementos sem nenhum aninhamento</span><span class="sxs-lookup"><span data-stu-id="a7435-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="a7435-130">Descreve como criar relações em um **Conjunto de Dados** entre elementos do Esquema XML que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="a7435-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="a7435-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a7435-131">Related Sections</span></span>  
 [<span data-ttu-id="a7435-132">Derivando a estrutura relacional do DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="a7435-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="a7435-133">Descreve a estrutura relacional, ou esquema, de um conjunto de **dados** que é criado a partir do esquema xml schema (XSD).</span><span class="sxs-lookup"><span data-stu-id="a7435-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="a7435-134">Mapeamento de restrições de esquema XML (XSD) para restrições de DataSet</span><span class="sxs-lookup"><span data-stu-id="a7435-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="a7435-135">Descreve os elementos de esquema XML usados para criar restrições de chave únicas e estrangeiras em um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="a7435-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7435-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="a7435-136">See also</span></span>

- [<span data-ttu-id="a7435-137">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a7435-137">ADO.NET Overview</span></span>](../ado-net-overview.md)

---
title: Gerar relações de DataSet do esquema XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 29c0e9ee96c376c6da392692febccbbae3c6a33f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034314"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="21f39-102">Gerar relações de DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="21f39-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="21f39-103">Em um <xref:System.Data.DataSet>, você forma uma associação entre dois ou mais colunas, criando uma relação pai-filho.</span><span class="sxs-lookup"><span data-stu-id="21f39-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="21f39-104">Há três maneiras de representar uma **conjunto de dados** relação dentro de um esquema XSD (linguagem) de definição de esquema XML:</span><span class="sxs-lookup"><span data-stu-id="21f39-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="21f39-105">Especifica tipos complexos aninhados.</span><span class="sxs-lookup"><span data-stu-id="21f39-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="21f39-106">Use o **msdata:Relationship** anotação.</span><span class="sxs-lookup"><span data-stu-id="21f39-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="21f39-107">Especifique um **xs: keyref** sem o **msdata:ConstraintOnly** anotação.</span><span class="sxs-lookup"><span data-stu-id="21f39-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="21f39-108">Tipos complexos aninhados</span><span class="sxs-lookup"><span data-stu-id="21f39-108">Nested Complex Types</span></span>  
 <span data-ttu-id="21f39-109">Definições de tipo complexo aninhado em um esquema indicam as relações pai-filho dos elementos.</span><span class="sxs-lookup"><span data-stu-id="21f39-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="21f39-110">O fragmento de esquema XML a seguir mostra que **OrderDetail** é um elemento filho do **ordem** elemento.</span><span class="sxs-lookup"><span data-stu-id="21f39-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="21f39-111">O processo de mapeamento de esquema XML cria tabelas na **conjunto de dados** que correspondem aos tipos aninhados complexos no esquema.</span><span class="sxs-lookup"><span data-stu-id="21f39-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="21f39-112">Ele também cria colunas adicionais que são usadas como pai**-** colunas filho para as tabelas geradas.</span><span class="sxs-lookup"><span data-stu-id="21f39-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="21f39-113">Observe que esses pai**-** colunas filho especificam relações, que não é o mesmo que especificar restrições de chave estrangeira/chave primária.</span><span class="sxs-lookup"><span data-stu-id="21f39-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="21f39-114">MSDATA:Relationship anotação</span><span class="sxs-lookup"><span data-stu-id="21f39-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="21f39-115">O **msdata:Relationship** anotação permite que você especifique explicitamente as relações pai-filho entre os elementos no esquema que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="21f39-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="21f39-116">O exemplo a seguir mostra a estrutura do **relação** elemento.</span><span class="sxs-lookup"><span data-stu-id="21f39-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="21f39-117">Os atributos do **msdata:Relationship** anotação identificar os elementos envolvidos na relação pai-filho, bem como o **parentkey** e **childkey** elementos e atributos envolvidos na relação.</span><span class="sxs-lookup"><span data-stu-id="21f39-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="21f39-118">O processo de mapeamento usa essas informações para gerar tabelas na **conjunto de dados** e criar a relação de chave estrangeira/chave primária entre essas tabelas.</span><span class="sxs-lookup"><span data-stu-id="21f39-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="21f39-119">Por exemplo, o fragmento de esquema a seguir especifica **ordem** e **OrderDetail** elementos no mesmo nível (não aninhado).</span><span class="sxs-lookup"><span data-stu-id="21f39-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="21f39-120">O esquema especifica um **msdata:Relationship** anotação, que especifica a relação pai-filho entre esses dois elementos.</span><span class="sxs-lookup"><span data-stu-id="21f39-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="21f39-121">Nesse caso, um relacionamento explícito deve ser especificado usando o **msdata:Relationship** anotação.</span><span class="sxs-lookup"><span data-stu-id="21f39-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="21f39-122">Usa o processo de mapeamento a **relacionamento** elemento para criar uma relação pai-filho entre os **OrderNumber** coluna no **ordem** tabela e o **OrderNo** coluna o **OrderDetail** na tabela a **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="21f39-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="21f39-123">O processo de mapeamento especifica apenas a relação; ele não automaticamente especificar quaisquer restrições nos valores nessas colunas, assim como as restrições de chave estrangeira/chave primárias em bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="21f39-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="21f39-124">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="21f39-124">In This Section</span></span>  
 [<span data-ttu-id="21f39-125">Mapear relações implícita entre elementos de esquema aninhados</span><span class="sxs-lookup"><span data-stu-id="21f39-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="21f39-126">Descreve as restrições e relações são criadas implicitamente em um **conjunto de dados** quando elementos aninhados são encontrados no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="21f39-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="21f39-127">Mapear relações definidas para elementos aninhados</span><span class="sxs-lookup"><span data-stu-id="21f39-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="21f39-128">Descreve como definir explicitamente as relações em um **conjunto de dados** para elementos aninhados no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="21f39-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="21f39-129">Especificar as relações entre os elementos sem nenhum aninhamento</span><span class="sxs-lookup"><span data-stu-id="21f39-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="21f39-130">Descreve como criar relações em um **conjunto de dados** entre os elementos de esquema XML que não estão aninhados.</span><span class="sxs-lookup"><span data-stu-id="21f39-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="21f39-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="21f39-131">Related Sections</span></span>  
 [<span data-ttu-id="21f39-132">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="21f39-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="21f39-133">Descreve a estrutura relacional ou o esquema de um **conjunto de dados** que é criado a partir do esquema de (XSD) de linguagem de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="21f39-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="21f39-134">Mapeamento de restrições de esquema XML (XSD) exclusivos para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="21f39-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="21f39-135">Descreve os elementos de esquema XML usados para criar restrições de chave estrangeiras e exclusivas em uma **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="21f39-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f39-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21f39-136">See also</span></span>

- <span data-ttu-id="21f39-137">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="21f39-137">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

---
title: Inferir relações
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: ee691eee95c34afdb6374cdd7448d4b44ece3055
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177560"
---
# <a name="inferring-relationships"></a><span data-ttu-id="24b1a-102">Inferir relações</span><span class="sxs-lookup"><span data-stu-id="24b1a-102">Inferring Relationships</span></span>

<span data-ttu-id="24b1a-103">Se um elemento que é inferido como uma tabela tiver um elemento filho que também é inferido como uma tabela, um <xref:System.Data.DataRelation> será criado entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="24b1a-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="24b1a-104">Uma nova coluna com um nome de **ParentTableName_Id** será adicionada à tabela criada para o elemento pai e a tabela criada para o elemento filho.</span><span class="sxs-lookup"><span data-stu-id="24b1a-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="24b1a-105">A propriedade **ColumnMapping** dessa coluna de identidade será definida como **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="24b1a-106">A coluna será uma chave primária de incremento automático para a tabela pai e será usada para a **DataRelation** entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="24b1a-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="24b1a-107">O tipo de dados da coluna de identidade adicionada será **System. Int32**, ao contrário do tipo de dados de todas as outras colunas inferidas, que é **System. String**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="24b1a-108">Um <xref:System.Data.ForeignKeyConstraint> with **DeleteRule**  =  **Cascade** também será criado usando a nova coluna nas tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="24b1a-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="24b1a-109">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="24b1a-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="24b1a-110">O processo de inferência produzirá duas tabelas: **Element1** e **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="24b1a-111">A tabela **Element1** terá duas colunas: **Element1_Id** e **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="24b1a-112">A propriedade **ColumnMapping** da coluna **Element1_Id** será definida como **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="24b1a-113">A propriedade **ColumnMapping** da coluna **ChildElement2** será definida como **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="24b1a-114">A coluna **Element1_Id** será definida como a chave primária da tabela **Element1** .</span><span class="sxs-lookup"><span data-stu-id="24b1a-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="24b1a-115">A tabela **ChildElement1** terá três colunas: **attr1**, **attr2** e **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="24b1a-116">A propriedade **ColumnMapping** para as colunas **attr1** e **attr2** será definida como **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="24b1a-117">A propriedade **ColumnMapping** da coluna **Element1_Id** será definida como **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="24b1a-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="24b1a-118">Uma **DataRelation** e **ForeignKeyConstraint** serão criadas usando as colunas **Element1_Id** de ambas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="24b1a-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="24b1a-119">**Conjunto** de um: DocumentElement</span><span class="sxs-lookup"><span data-stu-id="24b1a-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="24b1a-120">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="24b1a-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="24b1a-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="24b1a-121">Element1_Id</span></span>|<span data-ttu-id="24b1a-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="24b1a-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="24b1a-123">0</span><span class="sxs-lookup"><span data-stu-id="24b1a-123">0</span></span>|<span data-ttu-id="24b1a-124">Text2</span><span class="sxs-lookup"><span data-stu-id="24b1a-124">Text2</span></span>|  
  
 <span data-ttu-id="24b1a-125">**Tabela:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="24b1a-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="24b1a-126">attr1</span><span class="sxs-lookup"><span data-stu-id="24b1a-126">attr1</span></span>|<span data-ttu-id="24b1a-127">attr2</span><span class="sxs-lookup"><span data-stu-id="24b1a-127">attr2</span></span>|<span data-ttu-id="24b1a-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="24b1a-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="24b1a-129">value1</span><span class="sxs-lookup"><span data-stu-id="24b1a-129">value1</span></span>|<span data-ttu-id="24b1a-130">value2</span><span class="sxs-lookup"><span data-stu-id="24b1a-130">value2</span></span>|<span data-ttu-id="24b1a-131">0</span><span class="sxs-lookup"><span data-stu-id="24b1a-131">0</span></span>|  
  
 <span data-ttu-id="24b1a-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="24b1a-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="24b1a-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="24b1a-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="24b1a-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="24b1a-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="24b1a-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="24b1a-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="24b1a-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="24b1a-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="24b1a-137">**Aninhado:** True</span><span class="sxs-lookup"><span data-stu-id="24b1a-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="24b1a-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="24b1a-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="24b1a-139">**Coluna:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="24b1a-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="24b1a-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="24b1a-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="24b1a-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="24b1a-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="24b1a-142">**DeleteRule:** Cascade</span><span class="sxs-lookup"><span data-stu-id="24b1a-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="24b1a-143">**AcceptRejectRule:** None</span><span class="sxs-lookup"><span data-stu-id="24b1a-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b1a-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="24b1a-144">See also</span></span>

- [<span data-ttu-id="24b1a-145">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="24b1a-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="24b1a-146">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="24b1a-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="24b1a-147">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="24b1a-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="24b1a-148">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="24b1a-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="24b1a-149">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="24b1a-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="24b1a-150">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="24b1a-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="24b1a-151">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="24b1a-151">ADO.NET Overview</span></span>](../ado-net-overview.md)

---
title: Inferir relações
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 4c9c13453e4a830fcda337e8163649ba6491a995
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785369"
---
# <a name="inferring-relationships"></a><span data-ttu-id="319c7-102">Inferir relações</span><span class="sxs-lookup"><span data-stu-id="319c7-102">Inferring Relationships</span></span>
<span data-ttu-id="319c7-103">Se um elemento que é inferido como uma tabela tiver um elemento filho que também é inferido como uma tabela, um <xref:System.Data.DataRelation> será criado entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="319c7-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="319c7-104">Uma nova coluna com um nome de **ParentTableName_Id** será adicionada à tabela criada para o elemento pai e a tabela criada para o elemento filho.</span><span class="sxs-lookup"><span data-stu-id="319c7-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="319c7-105">A propriedade **ColumnMapping** dessa coluna de identidade será definida como **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="319c7-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="319c7-106">A coluna será uma chave primária de incremento automático para a tabela pai e será usada para a **DataRelation** entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="319c7-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="319c7-107">O tipo de dados da coluna de identidade adicionada será **System. Int32**, ao contrário do tipo de dados de todas as outras colunas inferidas, que é **System. String**.</span><span class="sxs-lookup"><span data-stu-id="319c7-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="319c7-108">Um <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** também será criado usando a nova coluna nas tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="319c7-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="319c7-109">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="319c7-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="319c7-110">O processo de inferência produzirá duas tabelas: **Element1** e **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="319c7-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="319c7-111">A tabela **Element1** terá duas colunas: **Element1_Id** e **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="319c7-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="319c7-112">A propriedade **ColumnMapping** da coluna **Element1_Id** será definida como **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="319c7-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="319c7-113">A propriedade **ColumnMapping** da coluna **ChildElement2** será definida como **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="319c7-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="319c7-114">A coluna **Element1_Id** será definida como a chave primária da tabela **Element1** .</span><span class="sxs-lookup"><span data-stu-id="319c7-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="319c7-115">A tabela **ChildElement1** terá três colunas: **attr1**, **attr2** e **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="319c7-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="319c7-116">A propriedade **ColumnMapping** para as colunas **attr1** e **attr2** será definida como **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="319c7-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="319c7-117">A propriedade **ColumnMapping** da coluna **Element1_Id** será definida como **MappingType. Hidden**.</span><span class="sxs-lookup"><span data-stu-id="319c7-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="319c7-118">Uma **DataRelation** e **ForeignKeyConstraint** serão criadas usando as colunas **Element1_Id** de ambas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="319c7-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="319c7-119">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="319c7-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="319c7-120">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="319c7-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="319c7-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="319c7-121">Element1_Id</span></span>|<span data-ttu-id="319c7-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="319c7-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="319c7-123">0</span><span class="sxs-lookup"><span data-stu-id="319c7-123">0</span></span>|<span data-ttu-id="319c7-124">Empresa2</span><span class="sxs-lookup"><span data-stu-id="319c7-124">Text2</span></span>|  
  
 <span data-ttu-id="319c7-125">**Tabela** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="319c7-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="319c7-126">attr1</span><span class="sxs-lookup"><span data-stu-id="319c7-126">attr1</span></span>|<span data-ttu-id="319c7-127">attr2</span><span class="sxs-lookup"><span data-stu-id="319c7-127">attr2</span></span>|<span data-ttu-id="319c7-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="319c7-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="319c7-129">value1</span><span class="sxs-lookup"><span data-stu-id="319c7-129">value1</span></span>|<span data-ttu-id="319c7-130">value2</span><span class="sxs-lookup"><span data-stu-id="319c7-130">value2</span></span>|<span data-ttu-id="319c7-131">0</span><span class="sxs-lookup"><span data-stu-id="319c7-131">0</span></span>|  
  
 <span data-ttu-id="319c7-132">**DataRelation** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="319c7-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="319c7-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="319c7-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="319c7-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="319c7-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="319c7-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="319c7-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="319c7-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="319c7-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="319c7-137">**Construção** verdadeiro</span><span class="sxs-lookup"><span data-stu-id="319c7-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="319c7-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="319c7-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="319c7-139">**Pilha** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="319c7-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="319c7-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="319c7-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="319c7-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="319c7-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="319c7-142">**DeleteRule:** Cascata</span><span class="sxs-lookup"><span data-stu-id="319c7-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="319c7-143">**AcceptRejectRule:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="319c7-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319c7-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="319c7-144">See also</span></span>

- [<span data-ttu-id="319c7-145">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="319c7-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="319c7-146">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="319c7-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="319c7-147">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="319c7-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="319c7-148">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="319c7-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- <span data-ttu-id="319c7-149">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="319c7-149">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="319c7-150">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="319c7-150">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="319c7-151">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="319c7-151">[ADO.NET Overview](../ado-net-overview.md)</span></span>

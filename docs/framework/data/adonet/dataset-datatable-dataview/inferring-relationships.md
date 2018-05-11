---
title: Inferência de relações
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 9833966fa5a16bef70a6ae2b9ca618fde0e05fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-relationships"></a><span data-ttu-id="aa608-102">Inferência de relações</span><span class="sxs-lookup"><span data-stu-id="aa608-102">Inferring Relationships</span></span>
<span data-ttu-id="aa608-103">Se um elemento que é inferido como uma tabela tem um elemento filho que também é inferido como uma tabela, um <xref:System.Data.DataRelation> será criada entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="aa608-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="aa608-104">Uma nova coluna com um nome de **ParentTableName_Id** será adicionada à tabela criada para o elemento pai e a tabela criada para o elemento filho.</span><span class="sxs-lookup"><span data-stu-id="aa608-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="aa608-105">O **ColumnMapping** definirá a propriedade desta coluna de identidade **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="aa608-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="aa608-106">A coluna será uma chave primária de incremento automático para a tabela pai e será usada para o **DataRelation** entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="aa608-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="aa608-107">O tipo de dados da coluna de identidade adicional será **System. Int32**, ao contrário do tipo de dados de todas as outras colunas deduzidos, que é **System. String**.</span><span class="sxs-lookup"><span data-stu-id="aa608-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="aa608-108">Um <xref:System.Data.ForeignKeyConstraint> com **DeleteRule** = **Cascade** também será criado usando a nova coluna nas tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="aa608-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="aa608-109">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="aa608-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="aa608-110">O processo de inferência produzirá duas tabelas: **Element1** e **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="aa608-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="aa608-111">O **Element1** tabela terá duas colunas: **Element1_Id** e **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="aa608-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="aa608-112">O **ColumnMapping** propriedade o **Element1_Id** coluna será definida como **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="aa608-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="aa608-113">O **ColumnMapping** propriedade o **ChildElement2** coluna será definida como **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="aa608-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="aa608-114">O **Element1_Id** coluna será definida como a chave primária do **Element1** tabela.</span><span class="sxs-lookup"><span data-stu-id="aa608-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="aa608-115">O **ChildElement1** tabela terá três colunas: **attr1**, **attr2** e **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="aa608-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="aa608-116">O **ColumnMapping** propriedade para o **attr1** e **attr2** colunas serão definidas como **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="aa608-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="aa608-117">O **ColumnMapping** propriedade o **Element1_Id** coluna será definida como **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="aa608-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="aa608-118">Um **DataRelation** e **ForeignKeyConstraint** será criado usando o **Element1_Id** colunas de ambas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="aa608-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="aa608-119">**Conjunto de dados:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="aa608-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="aa608-120">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="aa608-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="aa608-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="aa608-121">Element1_Id</span></span>|<span data-ttu-id="aa608-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="aa608-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="aa608-123">0</span><span class="sxs-lookup"><span data-stu-id="aa608-123">0</span></span>|<span data-ttu-id="aa608-124">Texto2</span><span class="sxs-lookup"><span data-stu-id="aa608-124">Text2</span></span>|  
  
 <span data-ttu-id="aa608-125">**Tabela:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="aa608-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="aa608-126">attr1</span><span class="sxs-lookup"><span data-stu-id="aa608-126">attr1</span></span>|<span data-ttu-id="aa608-127">attr2</span><span class="sxs-lookup"><span data-stu-id="aa608-127">attr2</span></span>|<span data-ttu-id="aa608-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="aa608-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="aa608-129">value1</span><span class="sxs-lookup"><span data-stu-id="aa608-129">value1</span></span>|<span data-ttu-id="aa608-130">value2</span><span class="sxs-lookup"><span data-stu-id="aa608-130">value2</span></span>|<span data-ttu-id="aa608-131">0</span><span class="sxs-lookup"><span data-stu-id="aa608-131">0</span></span>|  
  
 <span data-ttu-id="aa608-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="aa608-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="aa608-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="aa608-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="aa608-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="aa608-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="aa608-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="aa608-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="aa608-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="aa608-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="aa608-137">**Aninhados:** True</span><span class="sxs-lookup"><span data-stu-id="aa608-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="aa608-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="aa608-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="aa608-139">**Coluna:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="aa608-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="aa608-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="aa608-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="aa608-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="aa608-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="aa608-142">**DeleteRule:** em cascata</span><span class="sxs-lookup"><span data-stu-id="aa608-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="aa608-143">**AcceptRejectRule:** None</span><span class="sxs-lookup"><span data-stu-id="aa608-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa608-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa608-144">See Also</span></span>  
 [<span data-ttu-id="aa608-145">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="aa608-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="aa608-146">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="aa608-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="aa608-147">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="aa608-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="aa608-148">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="aa608-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="aa608-149">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="aa608-149">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="aa608-150">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="aa608-150">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="aa608-151">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="aa608-151">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

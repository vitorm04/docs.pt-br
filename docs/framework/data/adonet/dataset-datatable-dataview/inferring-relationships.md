---
title: Inferindo relações
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 2d25160b8dae8b8dc883abb589551782925ca325
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536276"
---
# <a name="inferring-relationships"></a><span data-ttu-id="285fd-102">Inferindo relações</span><span class="sxs-lookup"><span data-stu-id="285fd-102">Inferring Relationships</span></span>
<span data-ttu-id="285fd-103">Se um elemento que é inferido como uma tabela tem um elemento filho que também é inferido como uma tabela, um <xref:System.Data.DataRelation> será criada entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="285fd-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="285fd-104">Uma nova coluna com um nome de **ParentTableName_Id** será adicionado para a tabela criada para o elemento pai e a tabela criada para o elemento filho.</span><span class="sxs-lookup"><span data-stu-id="285fd-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="285fd-105">O **ColumnMapping** propriedade desta coluna de identidade será definida como **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="285fd-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="285fd-106">A coluna será uma chave primária de incremento automático para a tabela pai e será usada para o **DataRelation** entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="285fd-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="285fd-107">O tipo de dados da coluna de identidade adicionado estará **System.Int32**, ao contrário do tipo de dados de todas as outras colunas inferidos, que é **System. String**.</span><span class="sxs-lookup"><span data-stu-id="285fd-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="285fd-108">Um <xref:System.Data.ForeignKeyConstraint> com **DeleteRule** = **Cascade** também será criado usando a nova coluna nas tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="285fd-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="285fd-109">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="285fd-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="285fd-110">O processo de inferência produzirá duas tabelas: **Element1** e **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="285fd-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="285fd-111">O **Element1** tabela terá duas colunas: **Element1_Id** e **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="285fd-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="285fd-112">O **ColumnMapping** propriedade da **Element1_Id** coluna será definida como **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="285fd-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="285fd-113">O **ColumnMapping** propriedade da **ChildElement2** coluna será definida como **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="285fd-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="285fd-114">O **Element1_Id** coluna será definida como a chave primária da **Element1** tabela.</span><span class="sxs-lookup"><span data-stu-id="285fd-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="285fd-115">O **ChildElement1** tabela terá três colunas: **attr1**, **attr2** e **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="285fd-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="285fd-116">O **ColumnMapping** propriedade para o **attr1** e **attr2** colunas serão definidas como **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="285fd-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="285fd-117">O **ColumnMapping** propriedade da **Element1_Id** coluna será definida como **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="285fd-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="285fd-118">Um **DataRelation** e **ForeignKeyConstraint** será criado usando o **Element1_Id** colunas de ambas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="285fd-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="285fd-119">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="285fd-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="285fd-120">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="285fd-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="285fd-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="285fd-121">Element1_Id</span></span>|<span data-ttu-id="285fd-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="285fd-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="285fd-123">0</span><span class="sxs-lookup"><span data-stu-id="285fd-123">0</span></span>|<span data-ttu-id="285fd-124">Texto2</span><span class="sxs-lookup"><span data-stu-id="285fd-124">Text2</span></span>|  
  
 <span data-ttu-id="285fd-125">**Tabela:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="285fd-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="285fd-126">attr1</span><span class="sxs-lookup"><span data-stu-id="285fd-126">attr1</span></span>|<span data-ttu-id="285fd-127">attr2</span><span class="sxs-lookup"><span data-stu-id="285fd-127">attr2</span></span>|<span data-ttu-id="285fd-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="285fd-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="285fd-129">value1</span><span class="sxs-lookup"><span data-stu-id="285fd-129">value1</span></span>|<span data-ttu-id="285fd-130">value2</span><span class="sxs-lookup"><span data-stu-id="285fd-130">value2</span></span>|<span data-ttu-id="285fd-131">0</span><span class="sxs-lookup"><span data-stu-id="285fd-131">0</span></span>|  
  
 <span data-ttu-id="285fd-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="285fd-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="285fd-133">**ParentTable:** element1</span><span class="sxs-lookup"><span data-stu-id="285fd-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="285fd-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="285fd-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="285fd-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="285fd-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="285fd-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="285fd-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="285fd-137">**Aninhados:** verdadeiro</span><span class="sxs-lookup"><span data-stu-id="285fd-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="285fd-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="285fd-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="285fd-139">**Coluna:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="285fd-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="285fd-140">**ParentTable:** element1</span><span class="sxs-lookup"><span data-stu-id="285fd-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="285fd-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="285fd-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="285fd-142">**DeleteRule:** Cascata</span><span class="sxs-lookup"><span data-stu-id="285fd-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="285fd-143">**AcceptRejectRule:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="285fd-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="285fd-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="285fd-144">See also</span></span>
- [<span data-ttu-id="285fd-145">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="285fd-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="285fd-146">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="285fd-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="285fd-147">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="285fd-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="285fd-148">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="285fd-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- <span data-ttu-id="285fd-149">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="285fd-149">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="285fd-150">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="285fd-150">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="285fd-151">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="285fd-151">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

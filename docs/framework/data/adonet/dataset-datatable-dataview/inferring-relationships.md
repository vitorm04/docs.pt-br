---
title: Inferir relações
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: f8a9aba493dfe82466608ea60932ddfec5ef64f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879665"
---
# <a name="inferring-relationships"></a><span data-ttu-id="0922a-102">Inferir relações</span><span class="sxs-lookup"><span data-stu-id="0922a-102">Inferring Relationships</span></span>
<span data-ttu-id="0922a-103">Se um elemento que é inferido como uma tabela tem um elemento filho que também é inferido como uma tabela, um <xref:System.Data.DataRelation> será criada entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="0922a-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="0922a-104">Uma nova coluna com um nome de **ParentTableName_Id** será adicionado para a tabela criada para o elemento pai e a tabela criada para o elemento filho.</span><span class="sxs-lookup"><span data-stu-id="0922a-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="0922a-105">O **ColumnMapping** propriedade desta coluna de identidade será definida como **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="0922a-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="0922a-106">A coluna será uma chave primária de incremento automático para a tabela pai e será usada para o **DataRelation** entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="0922a-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="0922a-107">O tipo de dados da coluna de identidade adicionado estará **System.Int32**, ao contrário do tipo de dados de todas as outras colunas inferidos, que é **System. String**.</span><span class="sxs-lookup"><span data-stu-id="0922a-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="0922a-108">Um <xref:System.Data.ForeignKeyConstraint> com **DeleteRule** = **Cascade** também será criado usando a nova coluna nas tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="0922a-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="0922a-109">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="0922a-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0922a-110">O processo de inferência produzirá duas tabelas: **Element1** e **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="0922a-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="0922a-111">O **Element1** tabela terá duas colunas: **Element1_Id** e **ChildElement2**.</span><span class="sxs-lookup"><span data-stu-id="0922a-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="0922a-112">O **ColumnMapping** propriedade da **Element1_Id** coluna será definida como **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="0922a-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="0922a-113">O **ColumnMapping** propriedade da **ChildElement2** coluna será definida como **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="0922a-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="0922a-114">O **Element1_Id** coluna será definida como a chave primária da **Element1** tabela.</span><span class="sxs-lookup"><span data-stu-id="0922a-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="0922a-115">O **ChildElement1** tabela terá três colunas: **attr1**, **attr2** e **Element1_Id**.</span><span class="sxs-lookup"><span data-stu-id="0922a-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="0922a-116">O **ColumnMapping** propriedade para o **attr1** e **attr2** colunas serão definidas como **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="0922a-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="0922a-117">O **ColumnMapping** propriedade da **Element1_Id** coluna será definida como **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="0922a-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="0922a-118">Um **DataRelation** e **ForeignKeyConstraint** será criado usando o **Element1_Id** colunas de ambas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="0922a-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="0922a-119">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0922a-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0922a-120">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="0922a-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0922a-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0922a-121">Element1_Id</span></span>|<span data-ttu-id="0922a-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="0922a-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="0922a-123">0</span><span class="sxs-lookup"><span data-stu-id="0922a-123">0</span></span>|<span data-ttu-id="0922a-124">Texto2</span><span class="sxs-lookup"><span data-stu-id="0922a-124">Text2</span></span>|  
  
 <span data-ttu-id="0922a-125">**Tabela:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0922a-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="0922a-126">attr1</span><span class="sxs-lookup"><span data-stu-id="0922a-126">attr1</span></span>|<span data-ttu-id="0922a-127">attr2</span><span class="sxs-lookup"><span data-stu-id="0922a-127">attr2</span></span>|<span data-ttu-id="0922a-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0922a-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="0922a-129">value1</span><span class="sxs-lookup"><span data-stu-id="0922a-129">value1</span></span>|<span data-ttu-id="0922a-130">value2</span><span class="sxs-lookup"><span data-stu-id="0922a-130">value2</span></span>|<span data-ttu-id="0922a-131">0</span><span class="sxs-lookup"><span data-stu-id="0922a-131">0</span></span>|  
  
 <span data-ttu-id="0922a-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0922a-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="0922a-133">**ParentTable:** element1</span><span class="sxs-lookup"><span data-stu-id="0922a-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="0922a-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0922a-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="0922a-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0922a-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="0922a-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0922a-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="0922a-137">**Aninhados:** verdadeiro</span><span class="sxs-lookup"><span data-stu-id="0922a-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="0922a-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0922a-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="0922a-139">**Coluna:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="0922a-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="0922a-140">**ParentTable:** element1</span><span class="sxs-lookup"><span data-stu-id="0922a-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="0922a-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0922a-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="0922a-142">**DeleteRule:** Cascata</span><span class="sxs-lookup"><span data-stu-id="0922a-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="0922a-143">**AcceptRejectRule:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="0922a-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0922a-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0922a-144">See also</span></span>

- [<span data-ttu-id="0922a-145">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="0922a-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="0922a-146">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="0922a-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="0922a-147">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="0922a-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="0922a-148">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="0922a-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- <span data-ttu-id="0922a-149">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="0922a-149">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="0922a-150">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="0922a-150">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="0922a-151">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0922a-151">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

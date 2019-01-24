---
title: Inferindo tabelas
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: f777b225f9fbf4e8ce38778842d30a0a3054e22a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573486"
---
# <a name="inferring-tables"></a><span data-ttu-id="f2830-102">Inferindo tabelas</span><span class="sxs-lookup"><span data-stu-id="f2830-102">Inferring Tables</span></span>
<span data-ttu-id="f2830-103">Quando inferindo um esquema para um <xref:System.Data.DataSet> de um documento XML, ADO.NET primeiro determina quais elementos XML representam tabelas.</span><span class="sxs-lookup"><span data-stu-id="f2830-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="f2830-104">Estruturas XML a seguir resultam em uma tabela para o **conjunto de dados** esquema:</span><span class="sxs-lookup"><span data-stu-id="f2830-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="f2830-105">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="f2830-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="f2830-106">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="f2830-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="f2830-107">Elementos repetidos</span><span class="sxs-lookup"><span data-stu-id="f2830-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="f2830-108">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="f2830-108">Elements with Attributes</span></span>  
 <span data-ttu-id="f2830-109">Elementos que têm atributos especificados em que elas resultam em inferido tabelas.</span><span class="sxs-lookup"><span data-stu-id="f2830-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="f2830-110">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="f2830-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f2830-111">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="f2830-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f2830-112">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f2830-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f2830-113">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="f2830-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f2830-114">attr1</span><span class="sxs-lookup"><span data-stu-id="f2830-114">attr1</span></span>|<span data-ttu-id="f2830-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="f2830-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="f2830-116">value1</span><span class="sxs-lookup"><span data-stu-id="f2830-116">value1</span></span>||  
|<span data-ttu-id="f2830-117">value2</span><span class="sxs-lookup"><span data-stu-id="f2830-117">value2</span></span>|<span data-ttu-id="f2830-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="f2830-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="f2830-119">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="f2830-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="f2830-120">Elementos que têm resultados de elementos filho em inferido tabelas.</span><span class="sxs-lookup"><span data-stu-id="f2830-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="f2830-121">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="f2830-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f2830-122">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="f2830-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f2830-123">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f2830-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f2830-124">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="f2830-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f2830-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="f2830-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="f2830-126">Texto1</span><span class="sxs-lookup"><span data-stu-id="f2830-126">Text1</span></span>|  
  
 <span data-ttu-id="f2830-127">O resultado de elemento do documento ou raiz, em uma tabela inferida se ele tiver atributos ou elementos filho que são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="f2830-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="f2830-128">Se o elemento de documento tiver sem atributos e nenhum elemento filho que seria inferido como colunas, o elemento é inferido como uma **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="f2830-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="f2830-129">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="f2830-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f2830-130">O processo de inferência produz uma tabela chamada "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="f2830-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="f2830-131">**DataSet:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="f2830-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="f2830-132">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f2830-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="f2830-133">element1</span><span class="sxs-lookup"><span data-stu-id="f2830-133">Element1</span></span>|<span data-ttu-id="f2830-134">element2</span><span class="sxs-lookup"><span data-stu-id="f2830-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="f2830-135">Texto1</span><span class="sxs-lookup"><span data-stu-id="f2830-135">Text1</span></span>|<span data-ttu-id="f2830-136">Texto2</span><span class="sxs-lookup"><span data-stu-id="f2830-136">Text2</span></span>|  
  
 <span data-ttu-id="f2830-137">Como alternativa, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="f2830-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f2830-138">O processo de inferência produz um **conjunto de dados** denominado "DocumentElement" que contém uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="f2830-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="f2830-139">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f2830-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f2830-140">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="f2830-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f2830-141">attr1</span><span class="sxs-lookup"><span data-stu-id="f2830-141">attr1</span></span>|<span data-ttu-id="f2830-142">attr2</span><span class="sxs-lookup"><span data-stu-id="f2830-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="f2830-143">value1</span><span class="sxs-lookup"><span data-stu-id="f2830-143">value1</span></span>|<span data-ttu-id="f2830-144">value2</span><span class="sxs-lookup"><span data-stu-id="f2830-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="f2830-145">Elementos de repetição</span><span class="sxs-lookup"><span data-stu-id="f2830-145">Repeating Elements</span></span>  
 <span data-ttu-id="f2830-146">Elementos que se repetem o resultado em uma única tabela inferido.</span><span class="sxs-lookup"><span data-stu-id="f2830-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="f2830-147">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="f2830-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f2830-148">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="f2830-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f2830-149">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f2830-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f2830-150">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="f2830-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f2830-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="f2830-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="f2830-152">Texto1</span><span class="sxs-lookup"><span data-stu-id="f2830-152">Text1</span></span>|  
|<span data-ttu-id="f2830-153">Texto2</span><span class="sxs-lookup"><span data-stu-id="f2830-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2830-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2830-154">See also</span></span>
- [<span data-ttu-id="f2830-155">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="f2830-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="f2830-156">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="f2830-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="f2830-157">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="f2830-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="f2830-158">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="f2830-158">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="f2830-159">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="f2830-159">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="f2830-160">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f2830-160">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

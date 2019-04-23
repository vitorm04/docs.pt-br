---
title: Inferir tabelas
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 2c2a93d413f301dc3006b701e4bc7979a3fa7a1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181825"
---
# <a name="inferring-tables"></a><span data-ttu-id="1f3b2-102">Inferir tabelas</span><span class="sxs-lookup"><span data-stu-id="1f3b2-102">Inferring Tables</span></span>
<span data-ttu-id="1f3b2-103">Quando inferindo um esquema para um <xref:System.Data.DataSet> de um documento XML, ADO.NET primeiro determina quais elementos XML representam tabelas.</span><span class="sxs-lookup"><span data-stu-id="1f3b2-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="1f3b2-104">Estruturas XML a seguir resultam em uma tabela para o **conjunto de dados** esquema:</span><span class="sxs-lookup"><span data-stu-id="1f3b2-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="1f3b2-105">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="1f3b2-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="1f3b2-106">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="1f3b2-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="1f3b2-107">Elementos repetidos</span><span class="sxs-lookup"><span data-stu-id="1f3b2-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="1f3b2-108">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="1f3b2-108">Elements with Attributes</span></span>  
 <span data-ttu-id="1f3b2-109">Elementos que têm atributos especificados em que elas resultam em inferido tabelas.</span><span class="sxs-lookup"><span data-stu-id="1f3b2-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="1f3b2-110">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1f3b2-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1f3b2-111">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="1f3b2-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1f3b2-112">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1f3b2-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1f3b2-113">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1f3b2-114">attr1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-114">attr1</span></span>|<span data-ttu-id="1f3b2-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1f3b2-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="1f3b2-116">value1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-116">value1</span></span>||  
|<span data-ttu-id="1f3b2-117">value2</span><span class="sxs-lookup"><span data-stu-id="1f3b2-117">value2</span></span>|<span data-ttu-id="1f3b2-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="1f3b2-119">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="1f3b2-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="1f3b2-120">Elementos que têm resultados de elementos filho em inferido tabelas.</span><span class="sxs-lookup"><span data-stu-id="1f3b2-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="1f3b2-121">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1f3b2-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1f3b2-122">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="1f3b2-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1f3b2-123">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1f3b2-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1f3b2-124">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1f3b2-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="1f3b2-126">Texto1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-126">Text1</span></span>|  
  
 <span data-ttu-id="1f3b2-127">O resultado de elemento do documento ou raiz, em uma tabela inferida se ele tiver atributos ou elementos filho que são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="1f3b2-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="1f3b2-128">Se o elemento de documento tiver sem atributos e nenhum elemento filho que seria inferido como colunas, o elemento é inferido como uma **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="1f3b2-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="1f3b2-129">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1f3b2-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1f3b2-130">O processo de inferência produz uma tabela chamada "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="1f3b2-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="1f3b2-131">**DataSet:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="1f3b2-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="1f3b2-132">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1f3b2-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="1f3b2-133">element1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-133">Element1</span></span>|<span data-ttu-id="1f3b2-134">element2</span><span class="sxs-lookup"><span data-stu-id="1f3b2-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="1f3b2-135">Texto1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-135">Text1</span></span>|<span data-ttu-id="1f3b2-136">Texto2</span><span class="sxs-lookup"><span data-stu-id="1f3b2-136">Text2</span></span>|  
  
 <span data-ttu-id="1f3b2-137">Como alternativa, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1f3b2-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1f3b2-138">O processo de inferência produz um **conjunto de dados** denominado "DocumentElement" que contém uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="1f3b2-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="1f3b2-139">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1f3b2-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1f3b2-140">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1f3b2-141">attr1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-141">attr1</span></span>|<span data-ttu-id="1f3b2-142">attr2</span><span class="sxs-lookup"><span data-stu-id="1f3b2-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="1f3b2-143">value1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-143">value1</span></span>|<span data-ttu-id="1f3b2-144">value2</span><span class="sxs-lookup"><span data-stu-id="1f3b2-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="1f3b2-145">Elementos de repetição</span><span class="sxs-lookup"><span data-stu-id="1f3b2-145">Repeating Elements</span></span>  
 <span data-ttu-id="1f3b2-146">Elementos que se repetem o resultado em uma única tabela inferido.</span><span class="sxs-lookup"><span data-stu-id="1f3b2-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="1f3b2-147">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1f3b2-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1f3b2-148">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="1f3b2-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1f3b2-149">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1f3b2-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1f3b2-150">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1f3b2-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1f3b2-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="1f3b2-152">Texto1</span><span class="sxs-lookup"><span data-stu-id="1f3b2-152">Text1</span></span>|  
|<span data-ttu-id="1f3b2-153">Texto2</span><span class="sxs-lookup"><span data-stu-id="1f3b2-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f3b2-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f3b2-154">See also</span></span>

- [<span data-ttu-id="1f3b2-155">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="1f3b2-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="1f3b2-156">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="1f3b2-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="1f3b2-157">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="1f3b2-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="1f3b2-158">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="1f3b2-158">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="1f3b2-159">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="1f3b2-159">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="1f3b2-160">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1f3b2-160">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

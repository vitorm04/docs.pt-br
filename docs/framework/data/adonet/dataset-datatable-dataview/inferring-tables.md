---
title: Inferir tabelas
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 4a3d7b239dbc405cf2acae967b5be401dc772e38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177547"
---
# <a name="inferring-tables"></a><span data-ttu-id="1e8ee-102">Inferir tabelas</span><span class="sxs-lookup"><span data-stu-id="1e8ee-102">Inferring Tables</span></span>

<span data-ttu-id="1e8ee-103">Ao inferir um esquema para um <xref:System.Data.DataSet> de um documento XML, o ADO.net primeiro determina quais elementos XML representam tabelas.</span><span class="sxs-lookup"><span data-stu-id="1e8ee-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="1e8ee-104">As estruturas XML a seguir resultam em uma tabela para o esquema do **conjunto** de resultados:</span><span class="sxs-lookup"><span data-stu-id="1e8ee-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="1e8ee-105">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="1e8ee-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="1e8ee-106">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e8ee-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="1e8ee-107">Elementos repetitivos</span><span class="sxs-lookup"><span data-stu-id="1e8ee-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="1e8ee-108">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="1e8ee-108">Elements with Attributes</span></span>  

 <span data-ttu-id="1e8ee-109">Elementos que têm atributos especificados neles resultam em tabelas inferidas.</span><span class="sxs-lookup"><span data-stu-id="1e8ee-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="1e8ee-110">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1e8ee-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1e8ee-111">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="1e8ee-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1e8ee-112">**Conjunto** de um: DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1e8ee-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1e8ee-113">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1e8ee-114">attr1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-114">attr1</span></span>|<span data-ttu-id="1e8ee-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1e8ee-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="1e8ee-116">value1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-116">value1</span></span>||  
|<span data-ttu-id="1e8ee-117">value2</span><span class="sxs-lookup"><span data-stu-id="1e8ee-117">value2</span></span>|<span data-ttu-id="1e8ee-118">Text1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="1e8ee-119">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e8ee-119">Elements with Child Elements</span></span>  

 <span data-ttu-id="1e8ee-120">Elementos que têm elementos filho resultam em tabelas inferidas.</span><span class="sxs-lookup"><span data-stu-id="1e8ee-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="1e8ee-121">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1e8ee-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1e8ee-122">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="1e8ee-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1e8ee-123">**Conjunto** de um: DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1e8ee-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1e8ee-124">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1e8ee-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="1e8ee-126">Text1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-126">Text1</span></span>|  
  
 <span data-ttu-id="1e8ee-127">O elemento Document ou root resulta em uma tabela inferida se tiver atributos ou elementos filho que são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="1e8ee-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="1e8ee-128">Se o elemento Document não tiver nenhum atributo e nenhum elemento filho for inferido como Columns, o elemento será inferido como um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="1e8ee-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="1e8ee-129">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1e8ee-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1e8ee-130">O processo de inferência produz uma tabela denominada "documentElement".</span><span class="sxs-lookup"><span data-stu-id="1e8ee-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="1e8ee-131">**Conjunto** de um: NewDataSet</span><span class="sxs-lookup"><span data-stu-id="1e8ee-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="1e8ee-132">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1e8ee-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="1e8ee-133">Element1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-133">Element1</span></span>|<span data-ttu-id="1e8ee-134">Element2</span><span class="sxs-lookup"><span data-stu-id="1e8ee-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="1e8ee-135">Text1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-135">Text1</span></span>|<span data-ttu-id="1e8ee-136">Text2</span><span class="sxs-lookup"><span data-stu-id="1e8ee-136">Text2</span></span>|  
  
 <span data-ttu-id="1e8ee-137">Como alternativa, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1e8ee-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1e8ee-138">O processo de inferência produz um **conjunto de conjuntos** chamado "documentElement" que contém uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="1e8ee-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="1e8ee-139">**Conjunto** de um: DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1e8ee-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1e8ee-140">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1e8ee-141">attr1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-141">attr1</span></span>|<span data-ttu-id="1e8ee-142">attr2</span><span class="sxs-lookup"><span data-stu-id="1e8ee-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="1e8ee-143">value1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-143">value1</span></span>|<span data-ttu-id="1e8ee-144">value2</span><span class="sxs-lookup"><span data-stu-id="1e8ee-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="1e8ee-145">Elementos repetitivos</span><span class="sxs-lookup"><span data-stu-id="1e8ee-145">Repeating Elements</span></span>  

 <span data-ttu-id="1e8ee-146">Elementos que se repetem resultam em uma única tabela inferida.</span><span class="sxs-lookup"><span data-stu-id="1e8ee-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="1e8ee-147">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="1e8ee-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="1e8ee-148">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="1e8ee-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="1e8ee-149">**Conjunto** de um: DocumentElement</span><span class="sxs-lookup"><span data-stu-id="1e8ee-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="1e8ee-150">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="1e8ee-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="1e8ee-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="1e8ee-152">Text1</span><span class="sxs-lookup"><span data-stu-id="1e8ee-152">Text1</span></span>|  
|<span data-ttu-id="1e8ee-153">Text2</span><span class="sxs-lookup"><span data-stu-id="1e8ee-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e8ee-154">Veja também</span><span class="sxs-lookup"><span data-stu-id="1e8ee-154">See also</span></span>

- [<span data-ttu-id="1e8ee-155">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="1e8ee-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="1e8ee-156">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="1e8ee-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="1e8ee-157">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="1e8ee-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="1e8ee-158">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="1e8ee-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="1e8ee-159">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="1e8ee-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1e8ee-160">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1e8ee-160">ADO.NET Overview</span></span>](../ado-net-overview.md)

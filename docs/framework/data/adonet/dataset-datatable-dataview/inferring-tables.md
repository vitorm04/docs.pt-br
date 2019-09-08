---
title: Inferir tabelas
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 52ffd3fe90eb491dd01acf8538276cc828fdb309
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784483"
---
# <a name="inferring-tables"></a><span data-ttu-id="fc3c9-102">Inferir tabelas</span><span class="sxs-lookup"><span data-stu-id="fc3c9-102">Inferring Tables</span></span>
<span data-ttu-id="fc3c9-103">Ao inferir um esquema para um <xref:System.Data.DataSet> de um documento XML, o ADO.net primeiro determina quais elementos XML representam tabelas.</span><span class="sxs-lookup"><span data-stu-id="fc3c9-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="fc3c9-104">As estruturas XML a seguir resultam em uma tabela para o esquema do **conjunto** de resultados:</span><span class="sxs-lookup"><span data-stu-id="fc3c9-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="fc3c9-105">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="fc3c9-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="fc3c9-106">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="fc3c9-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="fc3c9-107">Elementos repetitivos</span><span class="sxs-lookup"><span data-stu-id="fc3c9-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="fc3c9-108">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="fc3c9-108">Elements with Attributes</span></span>  
 <span data-ttu-id="fc3c9-109">Elementos que têm atributos especificados neles resultam em tabelas inferidas.</span><span class="sxs-lookup"><span data-stu-id="fc3c9-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="fc3c9-110">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="fc3c9-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fc3c9-111">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="fc3c9-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="fc3c9-112">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fc3c9-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fc3c9-113">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fc3c9-114">attr1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-114">attr1</span></span>|<span data-ttu-id="fc3c9-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="fc3c9-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="fc3c9-116">value1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-116">value1</span></span>||  
|<span data-ttu-id="fc3c9-117">value2</span><span class="sxs-lookup"><span data-stu-id="fc3c9-117">value2</span></span>|<span data-ttu-id="fc3c9-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="fc3c9-119">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="fc3c9-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="fc3c9-120">Elementos que têm elementos filho resultam em tabelas inferidas.</span><span class="sxs-lookup"><span data-stu-id="fc3c9-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="fc3c9-121">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="fc3c9-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fc3c9-122">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="fc3c9-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="fc3c9-123">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fc3c9-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fc3c9-124">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fc3c9-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="fc3c9-126">Texto1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-126">Text1</span></span>|  
  
 <span data-ttu-id="fc3c9-127">O elemento Document ou root resulta em uma tabela inferida se tiver atributos ou elementos filho que são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="fc3c9-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="fc3c9-128">Se o elemento Document não tiver nenhum atributo e nenhum elemento filho for inferido como Columns, o elemento será inferido como um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="fc3c9-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="fc3c9-129">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="fc3c9-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fc3c9-130">O processo de inferência produz uma tabela denominada "documentElement".</span><span class="sxs-lookup"><span data-stu-id="fc3c9-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="fc3c9-131">**DataSet** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="fc3c9-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="fc3c9-132">**Tabela** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fc3c9-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="fc3c9-133">Element1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-133">Element1</span></span>|<span data-ttu-id="fc3c9-134">Element2</span><span class="sxs-lookup"><span data-stu-id="fc3c9-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="fc3c9-135">Texto1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-135">Text1</span></span>|<span data-ttu-id="fc3c9-136">Empresa2</span><span class="sxs-lookup"><span data-stu-id="fc3c9-136">Text2</span></span>|  
  
 <span data-ttu-id="fc3c9-137">Como alternativa, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="fc3c9-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fc3c9-138">O processo de inferência produz um **conjunto de conjuntos** chamado "documentElement" que contém uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="fc3c9-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="fc3c9-139">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fc3c9-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fc3c9-140">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fc3c9-141">attr1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-141">attr1</span></span>|<span data-ttu-id="fc3c9-142">attr2</span><span class="sxs-lookup"><span data-stu-id="fc3c9-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="fc3c9-143">value1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-143">value1</span></span>|<span data-ttu-id="fc3c9-144">value2</span><span class="sxs-lookup"><span data-stu-id="fc3c9-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="fc3c9-145">Elementos repetitivos</span><span class="sxs-lookup"><span data-stu-id="fc3c9-145">Repeating Elements</span></span>  
 <span data-ttu-id="fc3c9-146">Elementos que se repetem resultam em uma única tabela inferida.</span><span class="sxs-lookup"><span data-stu-id="fc3c9-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="fc3c9-147">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="fc3c9-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fc3c9-148">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="fc3c9-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="fc3c9-149">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fc3c9-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fc3c9-150">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fc3c9-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="fc3c9-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="fc3c9-152">Texto1</span><span class="sxs-lookup"><span data-stu-id="fc3c9-152">Text1</span></span>|  
|<span data-ttu-id="fc3c9-153">Empresa2</span><span class="sxs-lookup"><span data-stu-id="fc3c9-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc3c9-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc3c9-154">See also</span></span>

- [<span data-ttu-id="fc3c9-155">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="fc3c9-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="fc3c9-156">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="fc3c9-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="fc3c9-157">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="fc3c9-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="fc3c9-158">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="fc3c9-158">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="fc3c9-159">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="fc3c9-159">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="fc3c9-160">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="fc3c9-160">[ADO.NET Overview](../ado-net-overview.md)</span></span>

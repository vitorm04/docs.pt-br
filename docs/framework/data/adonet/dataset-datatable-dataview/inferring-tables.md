---
title: Inferir tabelas
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 2c2a93d413f301dc3006b701e4bc7979a3fa7a1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181825"
---
# <a name="inferring-tables"></a><span data-ttu-id="17ae0-102">Inferir tabelas</span><span class="sxs-lookup"><span data-stu-id="17ae0-102">Inferring Tables</span></span>
<span data-ttu-id="17ae0-103">Quando inferindo um esquema para um <xref:System.Data.DataSet> de um documento XML, ADO.NET primeiro determina quais elementos XML representam tabelas.</span><span class="sxs-lookup"><span data-stu-id="17ae0-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="17ae0-104">Estruturas XML a seguir resultam em uma tabela para o **conjunto de dados** esquema:</span><span class="sxs-lookup"><span data-stu-id="17ae0-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="17ae0-105">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="17ae0-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="17ae0-106">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="17ae0-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="17ae0-107">Elementos repetidos</span><span class="sxs-lookup"><span data-stu-id="17ae0-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="17ae0-108">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="17ae0-108">Elements with Attributes</span></span>  
 <span data-ttu-id="17ae0-109">Elementos que têm atributos especificados em que elas resultam em inferido tabelas.</span><span class="sxs-lookup"><span data-stu-id="17ae0-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="17ae0-110">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="17ae0-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="17ae0-111">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="17ae0-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="17ae0-112">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="17ae0-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="17ae0-113">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="17ae0-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="17ae0-114">attr1</span><span class="sxs-lookup"><span data-stu-id="17ae0-114">attr1</span></span>|<span data-ttu-id="17ae0-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="17ae0-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="17ae0-116">value1</span><span class="sxs-lookup"><span data-stu-id="17ae0-116">value1</span></span>||  
|<span data-ttu-id="17ae0-117">value2</span><span class="sxs-lookup"><span data-stu-id="17ae0-117">value2</span></span>|<span data-ttu-id="17ae0-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="17ae0-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="17ae0-119">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="17ae0-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="17ae0-120">Elementos que têm resultados de elementos filho em inferido tabelas.</span><span class="sxs-lookup"><span data-stu-id="17ae0-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="17ae0-121">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="17ae0-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="17ae0-122">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="17ae0-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="17ae0-123">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="17ae0-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="17ae0-124">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="17ae0-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="17ae0-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="17ae0-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="17ae0-126">Texto1</span><span class="sxs-lookup"><span data-stu-id="17ae0-126">Text1</span></span>|  
  
 <span data-ttu-id="17ae0-127">O resultado de elemento do documento ou raiz, em uma tabela inferida se ele tiver atributos ou elementos filho que são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="17ae0-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="17ae0-128">Se o elemento de documento tiver sem atributos e nenhum elemento filho que seria inferido como colunas, o elemento é inferido como uma **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="17ae0-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="17ae0-129">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="17ae0-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="17ae0-130">O processo de inferência produz uma tabela chamada "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="17ae0-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="17ae0-131">**DataSet:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="17ae0-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="17ae0-132">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="17ae0-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="17ae0-133">element1</span><span class="sxs-lookup"><span data-stu-id="17ae0-133">Element1</span></span>|<span data-ttu-id="17ae0-134">element2</span><span class="sxs-lookup"><span data-stu-id="17ae0-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="17ae0-135">Texto1</span><span class="sxs-lookup"><span data-stu-id="17ae0-135">Text1</span></span>|<span data-ttu-id="17ae0-136">Texto2</span><span class="sxs-lookup"><span data-stu-id="17ae0-136">Text2</span></span>|  
  
 <span data-ttu-id="17ae0-137">Como alternativa, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="17ae0-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="17ae0-138">O processo de inferência produz um **conjunto de dados** denominado "DocumentElement" que contém uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="17ae0-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="17ae0-139">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="17ae0-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="17ae0-140">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="17ae0-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="17ae0-141">attr1</span><span class="sxs-lookup"><span data-stu-id="17ae0-141">attr1</span></span>|<span data-ttu-id="17ae0-142">attr2</span><span class="sxs-lookup"><span data-stu-id="17ae0-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="17ae0-143">value1</span><span class="sxs-lookup"><span data-stu-id="17ae0-143">value1</span></span>|<span data-ttu-id="17ae0-144">value2</span><span class="sxs-lookup"><span data-stu-id="17ae0-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="17ae0-145">Elementos de repetição</span><span class="sxs-lookup"><span data-stu-id="17ae0-145">Repeating Elements</span></span>  
 <span data-ttu-id="17ae0-146">Elementos que se repetem o resultado em uma única tabela inferido.</span><span class="sxs-lookup"><span data-stu-id="17ae0-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="17ae0-147">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="17ae0-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="17ae0-148">O processo de inferência produz uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="17ae0-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="17ae0-149">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="17ae0-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="17ae0-150">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="17ae0-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="17ae0-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="17ae0-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="17ae0-152">Texto1</span><span class="sxs-lookup"><span data-stu-id="17ae0-152">Text1</span></span>|  
|<span data-ttu-id="17ae0-153">Texto2</span><span class="sxs-lookup"><span data-stu-id="17ae0-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17ae0-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17ae0-154">See also</span></span>

- [<span data-ttu-id="17ae0-155">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="17ae0-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="17ae0-156">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="17ae0-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="17ae0-157">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="17ae0-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="17ae0-158">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="17ae0-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="17ae0-159">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="17ae0-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="17ae0-160">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="17ae0-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Inferindo tabelas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2c00dd11d4d93e5d3b0e2f1c3b75765056a10cab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-tables"></a><span data-ttu-id="a0d65-102">Inferindo tabelas</span><span class="sxs-lookup"><span data-stu-id="a0d65-102">Inferring Tables</span></span>
<span data-ttu-id="a0d65-103">Quando inferir um esquema para um <xref:System.Data.DataSet> de um documento XML, ADO.NET primeiro determina quais elementos XML representam as tabelas.</span><span class="sxs-lookup"><span data-stu-id="a0d65-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="a0d65-104">Estruturas XML a seguir resultam em uma tabela para o **DataSet** esquema:</span><span class="sxs-lookup"><span data-stu-id="a0d65-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="a0d65-105">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="a0d65-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="a0d65-106">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="a0d65-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="a0d65-107">Elementos repetidos</span><span class="sxs-lookup"><span data-stu-id="a0d65-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="a0d65-108">Elementos com atributos</span><span class="sxs-lookup"><span data-stu-id="a0d65-108">Elements with Attributes</span></span>  
 <span data-ttu-id="a0d65-109">Elementos que têm atributos especificados no-los resultar em inferido tabelas.</span><span class="sxs-lookup"><span data-stu-id="a0d65-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="a0d65-110">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="a0d65-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a0d65-111">O processo de inferência produz uma tabela denominada "Element1".</span><span class="sxs-lookup"><span data-stu-id="a0d65-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a0d65-112">**Conjunto de dados:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a0d65-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a0d65-113">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="a0d65-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a0d65-114">attr1</span><span class="sxs-lookup"><span data-stu-id="a0d65-114">attr1</span></span>|<span data-ttu-id="a0d65-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="a0d65-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="a0d65-116">value1</span><span class="sxs-lookup"><span data-stu-id="a0d65-116">value1</span></span>||  
|<span data-ttu-id="a0d65-117">value2</span><span class="sxs-lookup"><span data-stu-id="a0d65-117">value2</span></span>|<span data-ttu-id="a0d65-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="a0d65-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="a0d65-119">Elementos com elementos filho</span><span class="sxs-lookup"><span data-stu-id="a0d65-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="a0d65-120">Elementos que têm resultados de elementos filho em inferido tabelas.</span><span class="sxs-lookup"><span data-stu-id="a0d65-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="a0d65-121">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="a0d65-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a0d65-122">O processo de inferência produz uma tabela denominada "Element1".</span><span class="sxs-lookup"><span data-stu-id="a0d65-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a0d65-123">**Conjunto de dados:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a0d65-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a0d65-124">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="a0d65-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a0d65-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a0d65-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="a0d65-126">Texto1</span><span class="sxs-lookup"><span data-stu-id="a0d65-126">Text1</span></span>|  
  
 <span data-ttu-id="a0d65-127">O resultado de elemento do documento ou raiz, em uma tabela deduzido se ele tem atributos ou elementos filho que são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="a0d65-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="a0d65-128">Se o elemento do documento sem atributos e não há elementos filho que poderiam ser inferidos como colunas, o elemento é inferido como um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="a0d65-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="a0d65-129">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="a0d65-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a0d65-130">O processo de inferência produz uma tabela denominada "DocumentElement."</span><span class="sxs-lookup"><span data-stu-id="a0d65-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="a0d65-131">**Conjunto de dados:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="a0d65-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="a0d65-132">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a0d65-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="a0d65-133">Element1</span><span class="sxs-lookup"><span data-stu-id="a0d65-133">Element1</span></span>|<span data-ttu-id="a0d65-134">Element2</span><span class="sxs-lookup"><span data-stu-id="a0d65-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="a0d65-135">Texto1</span><span class="sxs-lookup"><span data-stu-id="a0d65-135">Text1</span></span>|<span data-ttu-id="a0d65-136">Texto2</span><span class="sxs-lookup"><span data-stu-id="a0d65-136">Text2</span></span>|  
  
 <span data-ttu-id="a0d65-137">Como alternativa, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="a0d65-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a0d65-138">O processo de inferência produz um **DataSet** chamado "DocumentElement" que contém uma tabela chamada "Element1".</span><span class="sxs-lookup"><span data-stu-id="a0d65-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="a0d65-139">**Conjunto de dados:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a0d65-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a0d65-140">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="a0d65-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a0d65-141">attr1</span><span class="sxs-lookup"><span data-stu-id="a0d65-141">attr1</span></span>|<span data-ttu-id="a0d65-142">attr2</span><span class="sxs-lookup"><span data-stu-id="a0d65-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="a0d65-143">value1</span><span class="sxs-lookup"><span data-stu-id="a0d65-143">value1</span></span>|<span data-ttu-id="a0d65-144">value2</span><span class="sxs-lookup"><span data-stu-id="a0d65-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="a0d65-145">Elementos de repetição</span><span class="sxs-lookup"><span data-stu-id="a0d65-145">Repeating Elements</span></span>  
 <span data-ttu-id="a0d65-146">Elementos que se repetem resultará em uma única tabela inferida.</span><span class="sxs-lookup"><span data-stu-id="a0d65-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="a0d65-147">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="a0d65-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a0d65-148">O processo de inferência produz uma tabela denominada "Element1".</span><span class="sxs-lookup"><span data-stu-id="a0d65-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="a0d65-149">**Conjunto de dados:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a0d65-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a0d65-150">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="a0d65-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a0d65-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="a0d65-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="a0d65-152">Texto1</span><span class="sxs-lookup"><span data-stu-id="a0d65-152">Text1</span></span>|  
|<span data-ttu-id="a0d65-153">Texto2</span><span class="sxs-lookup"><span data-stu-id="a0d65-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0d65-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0d65-154">See Also</span></span>  
 [<span data-ttu-id="a0d65-155">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="a0d65-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="a0d65-156">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="a0d65-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="a0d65-157">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="a0d65-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="a0d65-158">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="a0d65-158">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="a0d65-159">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="a0d65-159">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="a0d65-160">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a0d65-160">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

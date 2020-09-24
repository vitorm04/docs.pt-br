---
title: Inferir o texto do elemento
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 7389e24f39902edf041c3cd3502303b17fd008ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164682"
---
# <a name="inferring-element-text"></a><span data-ttu-id="be245-102">Inferir o texto do elemento</span><span class="sxs-lookup"><span data-stu-id="be245-102">Inferring Element Text</span></span>

<span data-ttu-id="be245-103">Se um elemento contiver texto e não tiver nenhum elemento filho a ser inferido como tabelas (como elementos com atributos ou elementos repetidos), uma nova coluna com o nome **TableName_Text** será adicionada à tabela inferida para o elemento.</span><span class="sxs-lookup"><span data-stu-id="be245-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="be245-104">O texto contido no elemento será adicionado a uma linha na tabela e armazenado na nova coluna.</span><span class="sxs-lookup"><span data-stu-id="be245-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="be245-105">A propriedade **ColumnMapping** da nova coluna será definida como **MappingType. simpleContent**.</span><span class="sxs-lookup"><span data-stu-id="be245-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="be245-106">Por exemplo, considere o XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="be245-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="be245-107">O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas: **attr1** e **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="be245-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="be245-108">A propriedade **ColumnMapping** da coluna **attr1** será definida como **MappingType. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="be245-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="be245-109">A propriedade **ColumnMapping** da coluna **Element1_Text** será definida como **MappingType. simpleContent**.</span><span class="sxs-lookup"><span data-stu-id="be245-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="be245-110">**Conjunto** de um: DocumentElement</span><span class="sxs-lookup"><span data-stu-id="be245-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="be245-111">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="be245-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="be245-112">attr1</span><span class="sxs-lookup"><span data-stu-id="be245-112">attr1</span></span>|<span data-ttu-id="be245-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="be245-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="be245-114">value1</span><span class="sxs-lookup"><span data-stu-id="be245-114">value1</span></span>|<span data-ttu-id="be245-115">Text1</span><span class="sxs-lookup"><span data-stu-id="be245-115">Text1</span></span>|  
  
 <span data-ttu-id="be245-116">Se um elemento contiver texto, mas também tiver elementos filho que contenham texto, uma coluna não será adicionada à tabela para armazenar o texto contido no elemento.</span><span class="sxs-lookup"><span data-stu-id="be245-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="be245-117">O texto contido no elemento será ignorado, enquanto o texto nos elementos filho é incluído em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="be245-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="be245-118">Por exemplo, considere o XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="be245-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="be245-119">O processo de inferência produzirá uma tabela chamada **Element1** com uma coluna chamada **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="be245-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="be245-120">O texto do elemento **ChildElement1** será incluído em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="be245-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="be245-121">O outro texto será ignorado.</span><span class="sxs-lookup"><span data-stu-id="be245-121">The other text will be ignored.</span></span> <span data-ttu-id="be245-122">A propriedade **ColumnMapping** da coluna **ChildElement1** será definida como **MappingType. Element**.</span><span class="sxs-lookup"><span data-stu-id="be245-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="be245-123">**Conjunto** de um: DocumentElement</span><span class="sxs-lookup"><span data-stu-id="be245-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="be245-124">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="be245-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="be245-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="be245-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="be245-126">Text2</span><span class="sxs-lookup"><span data-stu-id="be245-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be245-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="be245-127">See also</span></span>

- [<span data-ttu-id="be245-128">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="be245-128">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="be245-129">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="be245-129">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="be245-130">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="be245-130">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="be245-131">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="be245-131">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="be245-132">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="be245-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="be245-133">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="be245-133">ADO.NET Overview</span></span>](../ado-net-overview.md)

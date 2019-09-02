---
title: Inferir o texto do elemento
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d8d64c0cbb0aecf736a54fa6816e286ab7efa191
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203533"
---
# <a name="inferring-element-text"></a><span data-ttu-id="3c74d-102">Inferir o texto do elemento</span><span class="sxs-lookup"><span data-stu-id="3c74d-102">Inferring Element Text</span></span>
<span data-ttu-id="3c74d-103">Se um elemento contiver texto e não tiver nenhum elemento filho a ser inferido como tabelas (como elementos com atributos ou elementos repetidos), uma nova coluna com o nome **TableName_Text** será adicionada à tabela inferida para o elemento.</span><span class="sxs-lookup"><span data-stu-id="3c74d-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="3c74d-104">O texto contido no elemento será adicionado a uma linha na tabela e armazenado na nova coluna.</span><span class="sxs-lookup"><span data-stu-id="3c74d-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="3c74d-105">A propriedade **ColumnMapping** da nova coluna será definida como MappingType **. simpleContent**.</span><span class="sxs-lookup"><span data-stu-id="3c74d-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="3c74d-106">Por exemplo, considere o XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c74d-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="3c74d-107">O processo de inferência produzirá uma tabela chamada **Element1** com duas colunas: **attr1** e **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="3c74d-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="3c74d-108">A propriedade **ColumnMapping** da coluna **attr1** será definida como MappingType **. Attribute**.</span><span class="sxs-lookup"><span data-stu-id="3c74d-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="3c74d-109">A propriedade **ColumnMapping** da coluna **Element1_Text** será definida como MappingType **. simpleContent**.</span><span class="sxs-lookup"><span data-stu-id="3c74d-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="3c74d-110">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="3c74d-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="3c74d-111">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="3c74d-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="3c74d-112">attr1</span><span class="sxs-lookup"><span data-stu-id="3c74d-112">attr1</span></span>|<span data-ttu-id="3c74d-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="3c74d-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="3c74d-114">value1</span><span class="sxs-lookup"><span data-stu-id="3c74d-114">value1</span></span>|<span data-ttu-id="3c74d-115">Texto1</span><span class="sxs-lookup"><span data-stu-id="3c74d-115">Text1</span></span>|  
  
 <span data-ttu-id="3c74d-116">Se um elemento contiver texto, mas também tiver elementos filho que contenham texto, uma coluna não será adicionada à tabela para armazenar o texto contido no elemento.</span><span class="sxs-lookup"><span data-stu-id="3c74d-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="3c74d-117">O texto contido no elemento será ignorado, enquanto o texto nos elementos filho é incluído em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="3c74d-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="3c74d-118">Por exemplo, considere o XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c74d-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="3c74d-119">O processo de inferência produzirá uma tabela chamada **Element1** com uma coluna chamada **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="3c74d-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="3c74d-120">O texto do elemento **ChildElement1** será incluído em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="3c74d-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="3c74d-121">O outro texto será ignorado.</span><span class="sxs-lookup"><span data-stu-id="3c74d-121">The other text will be ignored.</span></span> <span data-ttu-id="3c74d-122">A propriedade **ColumnMapping** da coluna **ChildElement1** será definida como MappingType **. Element**.</span><span class="sxs-lookup"><span data-stu-id="3c74d-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="3c74d-123">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="3c74d-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="3c74d-124">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="3c74d-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="3c74d-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="3c74d-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="3c74d-126">Empresa2</span><span class="sxs-lookup"><span data-stu-id="3c74d-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c74d-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c74d-127">See also</span></span>

- [<span data-ttu-id="3c74d-128">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="3c74d-128">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="3c74d-129">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="3c74d-129">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="3c74d-130">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="3c74d-130">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="3c74d-131">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="3c74d-131">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="3c74d-132">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="3c74d-132">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="3c74d-133">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3c74d-133">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

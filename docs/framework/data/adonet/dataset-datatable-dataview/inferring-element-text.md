---
title: Inferir o texto do elemento
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 6ffe8f2fbf01fbe8dfa9d78f3dfb9e39b6e80b16
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224956"
---
# <a name="inferring-element-text"></a><span data-ttu-id="33db8-102">Inferir o texto do elemento</span><span class="sxs-lookup"><span data-stu-id="33db8-102">Inferring Element Text</span></span>
<span data-ttu-id="33db8-103">Se um elemento contém o texto e não tem nenhum elemento filho seja inferido como tabelas, como (elementos com atributos) ou elementos repetidos, uma nova coluna com o nome **TableName_Text** será adicionada à tabela que é inferida para o elemento.</span><span class="sxs-lookup"><span data-stu-id="33db8-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="33db8-104">O texto contido no elemento será adicionado a uma linha na tabela e armazenado na nova coluna.</span><span class="sxs-lookup"><span data-stu-id="33db8-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="33db8-105">O **ColumnMapping** propriedade da nova coluna será definida como **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="33db8-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="33db8-106">Por exemplo, considere o seguinte XML.</span><span class="sxs-lookup"><span data-stu-id="33db8-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="33db8-107">O processo de inferência produzirá uma tabela denominada **Element1** com duas colunas: **attr1** e **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="33db8-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="33db8-108">O **ColumnMapping** propriedade da **attr1** coluna será definida como **MappingType.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="33db8-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="33db8-109">O **ColumnMapping** propriedade da **Element1_Text** coluna será definida como **MappingType.SimpleContent**.</span><span class="sxs-lookup"><span data-stu-id="33db8-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="33db8-110">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="33db8-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="33db8-111">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="33db8-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="33db8-112">attr1</span><span class="sxs-lookup"><span data-stu-id="33db8-112">attr1</span></span>|<span data-ttu-id="33db8-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="33db8-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="33db8-114">value1</span><span class="sxs-lookup"><span data-stu-id="33db8-114">value1</span></span>|<span data-ttu-id="33db8-115">Texto1</span><span class="sxs-lookup"><span data-stu-id="33db8-115">Text1</span></span>|  
  
 <span data-ttu-id="33db8-116">Se um elemento contém o texto, mas também tem elementos filho que contêm texto, uma coluna não será adicionada à tabela para armazenar o texto contido no elemento.</span><span class="sxs-lookup"><span data-stu-id="33db8-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="33db8-117">O texto contido no elemento será ignorado, enquanto o texto nos elementos filho é incluído em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="33db8-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="33db8-118">Por exemplo, considere o seguinte XML.</span><span class="sxs-lookup"><span data-stu-id="33db8-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="33db8-119">O processo de inferência produzirá uma tabela denominada **Element1** com uma coluna nomeada **ChildElement1**.</span><span class="sxs-lookup"><span data-stu-id="33db8-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="33db8-120">O texto para o **ChildElement1** elemento será incluído em uma linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="33db8-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="33db8-121">O outro texto será ignorado.</span><span class="sxs-lookup"><span data-stu-id="33db8-121">The other text will be ignored.</span></span> <span data-ttu-id="33db8-122">O **ColumnMapping** propriedade da **ChildElement1** coluna será definida como **MappingType.Element**.</span><span class="sxs-lookup"><span data-stu-id="33db8-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="33db8-123">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="33db8-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="33db8-124">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="33db8-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="33db8-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="33db8-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="33db8-126">Texto2</span><span class="sxs-lookup"><span data-stu-id="33db8-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33db8-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33db8-127">See also</span></span>

- [<span data-ttu-id="33db8-128">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="33db8-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="33db8-129">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="33db8-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="33db8-130">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="33db8-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="33db8-131">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="33db8-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="33db8-132">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="33db8-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="33db8-133">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="33db8-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

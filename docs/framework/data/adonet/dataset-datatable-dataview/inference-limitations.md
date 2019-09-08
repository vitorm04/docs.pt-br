---
title: Limitações de inferência
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 10347abc5b01edb4ec6fbf97221d44f4bfb88f54
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784579"
---
# <a name="inference-limitations"></a><span data-ttu-id="7ad66-102">Limitações de inferência</span><span class="sxs-lookup"><span data-stu-id="7ad66-102">Inference Limitations</span></span>
<span data-ttu-id="7ad66-103">O processo de inferir um <xref:System.Data.DataSet> esquema do XML pode resultar em esquemas diferentes dependendo dos elementos XML em cada documento.</span><span class="sxs-lookup"><span data-stu-id="7ad66-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="7ad66-104">Por exemplo, considere os documentos XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="7ad66-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="7ad66-105">Documento1</span><span class="sxs-lookup"><span data-stu-id="7ad66-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="7ad66-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="7ad66-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="7ad66-107">Para "Documento1", o processo de inferência produz um conjunto de um **DataSet** chamado "documentElement" e uma tabela chamada "Element1", porque "Element1" é um elemento repetitivo.</span><span class="sxs-lookup"><span data-stu-id="7ad66-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="7ad66-108">**DataSet** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="7ad66-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="7ad66-109">**Tabela** Element1</span><span class="sxs-lookup"><span data-stu-id="7ad66-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="7ad66-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="7ad66-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="7ad66-111">Texto1</span><span class="sxs-lookup"><span data-stu-id="7ad66-111">Text1</span></span>|  
|<span data-ttu-id="7ad66-112">Empresa2</span><span class="sxs-lookup"><span data-stu-id="7ad66-112">Text2</span></span>|  
  
 <span data-ttu-id="7ad66-113">No entanto, para "document2", o processo de inferência produz um **conjunto de conjuntos** chamado "NewDataSet" e uma tabela denominada "documentElement".</span><span class="sxs-lookup"><span data-stu-id="7ad66-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="7ad66-114">"Element1" é inferido como uma coluna porque não tem atributos nem elementos filho.</span><span class="sxs-lookup"><span data-stu-id="7ad66-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="7ad66-115">**DataSet** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="7ad66-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="7ad66-116">**Tabela** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="7ad66-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="7ad66-117">Element1</span><span class="sxs-lookup"><span data-stu-id="7ad66-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="7ad66-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="7ad66-118">Text1</span></span>|  
  
 <span data-ttu-id="7ad66-119">Esses dois documentos XML podem ter sido destinados a produzir o mesmo esquema, mas o processo de inferência produz resultados muito diferentes com base nos elementos contidos em cada documento.</span><span class="sxs-lookup"><span data-stu-id="7ad66-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="7ad66-120">Para evitar as discrepâncias que podem ocorrer ao gerar o esquema a partir de um documento XML, é recomendável especificar explicitamente um esquema usando XSD (linguagem de definição de esquema XML) ou XDR (XML-Data Reduced) ao carregar um **conjunto** de dados de XML.</span><span class="sxs-lookup"><span data-stu-id="7ad66-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="7ad66-121">Para obter mais informações sobre como especificar explicitamente um esquema de **conjunto** de dados com esquema XML, consulte [derivando a estrutura relacional do conjunto de dados do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7ad66-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad66-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ad66-122">See also</span></span>

- [<span data-ttu-id="7ad66-123">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="7ad66-123">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="7ad66-124">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="7ad66-124">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="7ad66-125">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="7ad66-125">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="7ad66-126">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="7ad66-126">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="7ad66-127">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="7ad66-127">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="7ad66-128">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="7ad66-128">[ADO.NET Overview](../ado-net-overview.md)</span></span>

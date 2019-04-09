---
title: Limitações de inferência
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 308d2ffdd9e2cb16626861e25613657f341a4ccb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076231"
---
# <a name="inference-limitations"></a><span data-ttu-id="b1a7d-102">Limitações de inferência</span><span class="sxs-lookup"><span data-stu-id="b1a7d-102">Inference Limitations</span></span>
<span data-ttu-id="b1a7d-103">O processo de inferir um <xref:System.Data.DataSet> esquema do XML pode resultar em esquemas diferentes, dependendo dos elementos XML em cada documento.</span><span class="sxs-lookup"><span data-stu-id="b1a7d-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="b1a7d-104">Por exemplo, considere os seguintes documentos XML.</span><span class="sxs-lookup"><span data-stu-id="b1a7d-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="b1a7d-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="b1a7d-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b1a7d-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="b1a7d-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b1a7d-107">Para "Documento1", o processo de inferência produz um **conjunto de dados** denominado "DocumentElement" e uma tabela chamada "Element1", como "Element1" é um elemento de repetição.</span><span class="sxs-lookup"><span data-stu-id="b1a7d-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="b1a7d-108">**DataSet:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b1a7d-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b1a7d-109">**Tabela:** element1</span><span class="sxs-lookup"><span data-stu-id="b1a7d-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b1a7d-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b1a7d-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="b1a7d-111">Texto1</span><span class="sxs-lookup"><span data-stu-id="b1a7d-111">Text1</span></span>|  
|<span data-ttu-id="b1a7d-112">Texto2</span><span class="sxs-lookup"><span data-stu-id="b1a7d-112">Text2</span></span>|  
  
 <span data-ttu-id="b1a7d-113">No entanto, para "Documento2", o processo de inferência produz um **conjunto de dados** denominado "NewDataSet" e uma tabela chamada "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="b1a7d-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="b1a7d-114">"Element1" é inferido como uma coluna porque ela tem nenhum atributo e nenhum elemento filho.</span><span class="sxs-lookup"><span data-stu-id="b1a7d-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="b1a7d-115">**DataSet:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="b1a7d-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="b1a7d-116">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b1a7d-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="b1a7d-117">element1</span><span class="sxs-lookup"><span data-stu-id="b1a7d-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="b1a7d-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="b1a7d-118">Text1</span></span>|  
  
 <span data-ttu-id="b1a7d-119">Esses dois documentos XML podem ser o esperado para produzir o mesmo esquema, mas o processo de inferência produz resultados muito diferentes com base em elementos contidos em cada documento.</span><span class="sxs-lookup"><span data-stu-id="b1a7d-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="b1a7d-120">Para evitar as discrepâncias que podem ocorrer ao gerar o esquema de um documento XML, é recomendável que você especifique explicitamente um esquema usando a linguagem de definição de esquema XML (XSD) ou XML-Data Reduced (XDR) ao carregar uma **conjunto de dados** de XML.</span><span class="sxs-lookup"><span data-stu-id="b1a7d-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="b1a7d-121">Para obter mais informações sobre como especificar explicitamente uma **DataSet** esquema com o esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="b1a7d-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a7d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1a7d-122">See also</span></span>

- [<span data-ttu-id="b1a7d-123">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="b1a7d-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="b1a7d-124">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="b1a7d-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="b1a7d-125">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="b1a7d-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="b1a7d-126">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="b1a7d-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="b1a7d-127">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="b1a7d-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="b1a7d-128">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="b1a7d-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Limitações de inferência
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: d113df98cdd339300b3e75ceda49a56d4f346d3c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190669"
---
# <a name="inference-limitations"></a><span data-ttu-id="7d8eb-102">Limitações de inferência</span><span class="sxs-lookup"><span data-stu-id="7d8eb-102">Inference Limitations</span></span>
<span data-ttu-id="7d8eb-103">O processo de inferir um <xref:System.Data.DataSet> esquema do XML pode resultar em esquemas diferentes, dependendo dos elementos XML em cada documento.</span><span class="sxs-lookup"><span data-stu-id="7d8eb-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="7d8eb-104">Por exemplo, considere os seguintes documentos XML.</span><span class="sxs-lookup"><span data-stu-id="7d8eb-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="7d8eb-105">Documento1:</span><span class="sxs-lookup"><span data-stu-id="7d8eb-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="7d8eb-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="7d8eb-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="7d8eb-107">Para "Documento1", o processo de inferência produz um **conjunto de dados** denominado "DocumentElement" e uma tabela chamada "Element1", como "Element1" é um elemento de repetição.</span><span class="sxs-lookup"><span data-stu-id="7d8eb-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="7d8eb-108">**Conjunto de dados:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="7d8eb-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="7d8eb-109">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="7d8eb-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="7d8eb-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="7d8eb-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="7d8eb-111">Texto1</span><span class="sxs-lookup"><span data-stu-id="7d8eb-111">Text1</span></span>|  
|<span data-ttu-id="7d8eb-112">Texto2</span><span class="sxs-lookup"><span data-stu-id="7d8eb-112">Text2</span></span>|  
  
 <span data-ttu-id="7d8eb-113">No entanto, para "Documento2", o processo de inferência produz um **conjunto de dados** denominado "NewDataSet" e uma tabela chamada "DocumentElement".</span><span class="sxs-lookup"><span data-stu-id="7d8eb-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="7d8eb-114">"Element1" é inferido como uma coluna porque ela tem nenhum atributo e nenhum elemento filho.</span><span class="sxs-lookup"><span data-stu-id="7d8eb-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="7d8eb-115">**Conjunto de dados:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="7d8eb-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="7d8eb-116">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="7d8eb-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="7d8eb-117">element1</span><span class="sxs-lookup"><span data-stu-id="7d8eb-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="7d8eb-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="7d8eb-118">Text1</span></span>|  
  
 <span data-ttu-id="7d8eb-119">Esses dois documentos XML podem ser o esperado para produzir o mesmo esquema, mas o processo de inferência produz resultados muito diferentes com base em elementos contidos em cada documento.</span><span class="sxs-lookup"><span data-stu-id="7d8eb-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="7d8eb-120">Para evitar as discrepâncias que podem ocorrer ao gerar o esquema de um documento XML, é recomendável que você especifique explicitamente um esquema usando a linguagem de definição de esquema XML (XSD) ou XML-Data Reduced (XDR) ao carregar uma **conjunto de dados** de XML.</span><span class="sxs-lookup"><span data-stu-id="7d8eb-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="7d8eb-121">Para obter mais informações sobre como especificar explicitamente uma **DataSet** esquema com o esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="7d8eb-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d8eb-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d8eb-122">See Also</span></span>  
 [<span data-ttu-id="7d8eb-123">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="7d8eb-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="7d8eb-124">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="7d8eb-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="7d8eb-125">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="7d8eb-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="7d8eb-126">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="7d8eb-126">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="7d8eb-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="7d8eb-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="7d8eb-128">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="7d8eb-128">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

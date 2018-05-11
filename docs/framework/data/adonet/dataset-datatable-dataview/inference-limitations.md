---
title: Limitações de inferência
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: b3ad1e66a6a1a4cb2a2aab7b2f86f38e5c784876
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="inference-limitations"></a><span data-ttu-id="f0a51-102">Limitações de inferência</span><span class="sxs-lookup"><span data-stu-id="f0a51-102">Inference Limitations</span></span>
<span data-ttu-id="f0a51-103">O processo de inferir um <xref:System.Data.DataSet> esquema do XML pode resultar em esquemas diferentes dependendo das elementos XML de cada documento.</span><span class="sxs-lookup"><span data-stu-id="f0a51-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="f0a51-104">Por exemplo, considere os seguintes documentos XML.</span><span class="sxs-lookup"><span data-stu-id="f0a51-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="f0a51-105">Documento1:</span><span class="sxs-lookup"><span data-stu-id="f0a51-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f0a51-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="f0a51-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f0a51-107">Para "Documento1", o processo de inferência produz um **DataSet** chamado "DocumentElement" e uma tabela denominada "Element1", como "Element1" é um elemento de repetição.</span><span class="sxs-lookup"><span data-stu-id="f0a51-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="f0a51-108">**Conjunto de dados:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f0a51-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f0a51-109">**Tabela:** Element1</span><span class="sxs-lookup"><span data-stu-id="f0a51-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f0a51-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="f0a51-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="f0a51-111">Texto1</span><span class="sxs-lookup"><span data-stu-id="f0a51-111">Text1</span></span>|  
|<span data-ttu-id="f0a51-112">Texto2</span><span class="sxs-lookup"><span data-stu-id="f0a51-112">Text2</span></span>|  
  
 <span data-ttu-id="f0a51-113">No entanto, para "Documento2", o processo de inferência produz um **DataSet** chamado "NewDataSet" e uma tabela denominada "DocumentElement."</span><span class="sxs-lookup"><span data-stu-id="f0a51-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="f0a51-114">"Element1" será inferida como uma coluna porque ela tem nenhum atributo e nenhum elemento filho.</span><span class="sxs-lookup"><span data-stu-id="f0a51-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="f0a51-115">**Conjunto de dados:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="f0a51-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="f0a51-116">**Tabela:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f0a51-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="f0a51-117">Element1</span><span class="sxs-lookup"><span data-stu-id="f0a51-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="f0a51-118">Texto1</span><span class="sxs-lookup"><span data-stu-id="f0a51-118">Text1</span></span>|  
  
 <span data-ttu-id="f0a51-119">Esses dois documentos XML podem ter sido a intenção para produzir o mesmo esquema, mas o processo de inferência produz resultados muito diferentes com base nos elementos contidos em cada documento.</span><span class="sxs-lookup"><span data-stu-id="f0a51-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="f0a51-120">Para evitar as discrepâncias que podem ocorrer durante a geração de esquema de um documento XML, é recomendável que você especifique explicitamente um esquema usando a linguagem de definição de esquema XML (XSD) ou XML-Data Reduced (XDR) ao carregar um **conjunto de dados** de XML.</span><span class="sxs-lookup"><span data-stu-id="f0a51-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="f0a51-121">Para obter mais informações sobre como especificar explicitamente um **DataSet** de esquema com o esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="f0a51-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0a51-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0a51-122">See Also</span></span>  
 [<span data-ttu-id="f0a51-123">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="f0a51-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="f0a51-124">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="f0a51-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="f0a51-125">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="f0a51-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="f0a51-126">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="f0a51-126">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="f0a51-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="f0a51-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="f0a51-128">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f0a51-128">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>

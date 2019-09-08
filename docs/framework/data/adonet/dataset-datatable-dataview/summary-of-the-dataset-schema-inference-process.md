---
title: Resumo do processo de inferência de esquema de DataSet
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: b0dd22412ddda86aa2883a26353abb1516a94e17
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785949"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="c144a-102">Resumo do processo de inferência de esquema de DataSet</span><span class="sxs-lookup"><span data-stu-id="c144a-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="c144a-103">O processo de inferência determina primeiro, a partir do documento XML, quais elementos serão inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="c144a-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="c144a-104">Do XML restante, o processo de inferência determina as colunas para essas tabelas.</span><span class="sxs-lookup"><span data-stu-id="c144a-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="c144a-105">Para tabelas aninhadas, o processo de inferência <xref:System.Data.ForeignKeyConstraint> gera objetos aninhados <xref:System.Data.DataRelation> e.</span><span class="sxs-lookup"><span data-stu-id="c144a-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="c144a-106">Veja a seguir um breve resumo das regras de inferência:</span><span class="sxs-lookup"><span data-stu-id="c144a-106">Following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="c144a-107">Elementos que têm atributos são inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="c144a-107">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="c144a-108">Elementos que têm elementos filho são inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="c144a-108">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="c144a-109">Elementos que se repetem são inferidos como uma única tabela.</span><span class="sxs-lookup"><span data-stu-id="c144a-109">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="c144a-110">Se o documento, ou raiz, o elemento não tiver atributos e nenhum elemento filho que fosse inferido como colunas, ele será inferido como um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c144a-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c144a-111">Caso contrário, o elemento Document é inferido como uma tabela.</span><span class="sxs-lookup"><span data-stu-id="c144a-111">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="c144a-112">Os atributos são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="c144a-112">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="c144a-113">Elementos que não têm atributos ou elementos filho, e que não se repetem, são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="c144a-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="c144a-114">Para elementos que são inferidos como tabelas aninhadas dentro de outros elementos que também são inferidos como tabelas, uma **DataRelation** aninhada é criada entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="c144a-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="c144a-115">Uma nova coluna de chave primária chamada **TableName_Id** é adicionada às duas tabelas e usada pela **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="c144a-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="c144a-116">Um **ForeignKeyConstraint** é criado entre as duas tabelas usando a coluna **TableName_Id** .</span><span class="sxs-lookup"><span data-stu-id="c144a-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="c144a-117">Para elementos que são inferidos como tabelas e que contêm texto, mas não têm elementos filho, uma nova coluna chamada **TableName_Text** é criada para o texto de cada um dos elementos.</span><span class="sxs-lookup"><span data-stu-id="c144a-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="c144a-118">Se um elemento for inferido como uma tabela e tiver texto, mas também tiver elementos filho, o texto será ignorado.</span><span class="sxs-lookup"><span data-stu-id="c144a-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c144a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c144a-119">See also</span></span>

- [<span data-ttu-id="c144a-120">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="c144a-120">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="c144a-121">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="c144a-121">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="c144a-122">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="c144a-122">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="c144a-123">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="c144a-123">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="c144a-124">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="c144a-124">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="c144a-125">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c144a-125">[ADO.NET Overview](../ado-net-overview.md)</span></span>

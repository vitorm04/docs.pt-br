---
title: Resumo do processo de inferência de esquema de DataSet
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 272e5762b7afd9f3ab24cbdec5f31bb120364815
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116058"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="338d4-102">Resumo do processo de inferência de esquema de DataSet</span><span class="sxs-lookup"><span data-stu-id="338d4-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="338d4-103">O processo de inferência primeiro determina, do documento XML, quais elementos serão inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="338d4-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="338d4-104">Do XML restante, o processo de inferência determina as colunas para essas tabelas.</span><span class="sxs-lookup"><span data-stu-id="338d4-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="338d4-105">Para tabelas aninhadas, gera o processo de inferência de tipos aninhados <xref:System.Data.DataRelation> e <xref:System.Data.ForeignKeyConstraint> objetos.</span><span class="sxs-lookup"><span data-stu-id="338d4-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="338d4-106">A seguir está um breve resumo de regras de inferência:</span><span class="sxs-lookup"><span data-stu-id="338d4-106">Following is a brief summary of inference rules:</span></span>  
  
-   <span data-ttu-id="338d4-107">Elementos que têm atributos são inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="338d4-107">Elements that have attributes are inferred as tables.</span></span>  
  
-   <span data-ttu-id="338d4-108">Elementos que têm elementos filho são inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="338d4-108">Elements that have child elements are inferred as tables.</span></span>  
  
-   <span data-ttu-id="338d4-109">Elementos que se repetem são inferidos como uma única tabela.</span><span class="sxs-lookup"><span data-stu-id="338d4-109">Elements that repeat are inferred as a single table.</span></span>  
  
-   <span data-ttu-id="338d4-110">Se o elemento de documento ou raiz, tem nenhum atributo e nenhum elemento filho que seria inferido como colunas, ele será inferido como um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="338d4-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="338d4-111">Caso contrário, o elemento do documento é inferido como uma tabela.</span><span class="sxs-lookup"><span data-stu-id="338d4-111">Otherwise, the document element is inferred as a table.</span></span>  
  
-   <span data-ttu-id="338d4-112">Atributos são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="338d4-112">Attributes are inferred as columns.</span></span>  
  
-   <span data-ttu-id="338d4-113">Elementos que não têm atributos ou elementos filho e que não se repetem, são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="338d4-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
-   <span data-ttu-id="338d4-114">Para elementos que são inferidos como tabelas aninhadas dentro de outros elementos que também sejam inferidos como tabelas, um aninhado **DataRelation** é criada entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="338d4-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="338d4-115">Uma coluna de chave primária, novo chamada **TableName_Id** é adicionado para ambas as tabelas e usado pela **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="338d4-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="338d4-116">Um **ForeignKeyConstraint** é criada entre as duas tabelas usando o **TableName_Id** coluna.</span><span class="sxs-lookup"><span data-stu-id="338d4-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
-   <span data-ttu-id="338d4-117">Para elementos que são inferidos como tabelas e que contêm texto, mas que nenhum elemento filho, uma nova coluna chamada **TableName_Text** é criado para o texto de cada um dos elementos.</span><span class="sxs-lookup"><span data-stu-id="338d4-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="338d4-118">Se um elemento é inferido como uma tabela e tem o texto, mas também tem elementos filho, o texto será ignorado.</span><span class="sxs-lookup"><span data-stu-id="338d4-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="338d4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="338d4-119">See also</span></span>

- [<span data-ttu-id="338d4-120">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="338d4-120">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="338d4-121">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="338d4-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="338d4-122">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="338d4-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="338d4-123">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="338d4-123">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="338d4-124">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="338d4-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="338d4-125">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="338d4-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

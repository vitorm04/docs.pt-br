---
title: Suporte à herança
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 668f4f1dd284550e644ce6b8a4491ca47105575e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230909"
---
# <a name="inheritance-support"></a><span data-ttu-id="e75e7-102">Suporte à herança</span><span class="sxs-lookup"><span data-stu-id="e75e7-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e75e7-103">dá suporte a *mapeamento de tabela única*.</span><span class="sxs-lookup"><span data-stu-id="e75e7-103">supports *single-table mapping*.</span></span> <span data-ttu-id="e75e7-104">Ou seja uma hierarquia completa de herança é armazenada em uma única tabela de base de dados.</span><span class="sxs-lookup"><span data-stu-id="e75e7-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="e75e7-105">A tabela contém aplainada a união de todas as colunas de dados possíveis para a hierarquia inteira.</span><span class="sxs-lookup"><span data-stu-id="e75e7-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="e75e7-106">(A união de é o resultado de combinar duas tabelas em uma tabela que possui as linhas que estaram presente em qualquer uma das tabelas originais.) Cada linha tem nulos em colunas que não se aplicam ao tipo da instância representada por linha.</span><span class="sxs-lookup"><span data-stu-id="e75e7-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="e75e7-107">A estratégia de mapeamento de tabela única é a representação mais simples de herança e fornece características de desempenho bom para várias categorias diferentes de consultas.</span><span class="sxs-lookup"><span data-stu-id="e75e7-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="e75e7-108">Para implementar esse mapeamento em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você deve especificar atributos e propriedades de atributo na classe raiz da hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="e75e7-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="e75e7-109">Para obter mais informações, confira [Como: Mapear hierarquias de herança](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="e75e7-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="e75e7-110">Os desenvolvedores usando o Visual Studio também podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para mapear hierarquias de herança.</span><span class="sxs-lookup"><span data-stu-id="e75e7-110">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75e7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e75e7-111">See also</span></span>

- [<span data-ttu-id="e75e7-112">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="e75e7-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

---
title: Suporte à herança
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 7673e69458d5c1af854747c43ba463332a9cd588
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158247"
---
# <a name="inheritance-support"></a><span data-ttu-id="68e2c-102">Suporte à herança</span><span class="sxs-lookup"><span data-stu-id="68e2c-102">Inheritance Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="68e2c-103">dá suporte ao *mapeamento de tabela única*.</span><span class="sxs-lookup"><span data-stu-id="68e2c-103">supports *single-table mapping*.</span></span> <span data-ttu-id="68e2c-104">Ou seja uma hierarquia completa de herança é armazenada em uma única tabela de base de dados.</span><span class="sxs-lookup"><span data-stu-id="68e2c-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="68e2c-105">A tabela contém aplainada a união de todas as colunas de dados possíveis para a hierarquia inteira.</span><span class="sxs-lookup"><span data-stu-id="68e2c-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="68e2c-106">(Uma União é o resultado da combinação de duas tabelas em uma tabela que tem as linhas que estavam presentes em qualquer uma das tabelas originais.) Cada linha tem nulos nas colunas que não se aplicam ao tipo da instância representada pela linha.</span><span class="sxs-lookup"><span data-stu-id="68e2c-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="68e2c-107">A estratégia de mapeamento de tabela única é a representação mais simples de herança e fornece características de desempenho bom para várias categorias diferentes de consultas.</span><span class="sxs-lookup"><span data-stu-id="68e2c-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="68e2c-108">Para implementar esse mapeamento em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você deve especificar atributos e propriedades de atributo na classe raiz da hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="68e2c-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="68e2c-109">Para obter mais informações, consulte [como mapear hierarquias de herança](how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="68e2c-109">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="68e2c-110">Os desenvolvedores que usam o Visual Studio também podem usar o Object Relational Designer para mapear hierarquias de herança.</span><span class="sxs-lookup"><span data-stu-id="68e2c-110">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e2c-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="68e2c-111">See also</span></span>

- [<span data-ttu-id="68e2c-112">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="68e2c-112">Background Information</span></span>](background-information.md)

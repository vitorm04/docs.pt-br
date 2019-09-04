---
title: Funções (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: ec94a0f16fb3b836297f6675cc938a711816555b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250915"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="ff496-102">Funções (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ff496-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="ff496-103">Entity SQL oferece suporte funções definidas pelo usuário, funções, canônicas e funções específicos do provedor.</span><span class="sxs-lookup"><span data-stu-id="ff496-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="ff496-104">As funções definidas pelo usuário são especificadas no modelo conceitual ou embutido na consulta.</span><span class="sxs-lookup"><span data-stu-id="ff496-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="ff496-105">Para obter mais informações, consulte [funções definidas pelo usuário](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ff496-105">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="ff496-106">As funções canônicas são predefinidas em Entity Framework e devem ser suportados por provedores de dados.</span><span class="sxs-lookup"><span data-stu-id="ff496-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="ff496-107">Os comandos de Entity SQL irão falhar se um usuário chama uma função que não é suportada por um provedor.</span><span class="sxs-lookup"><span data-stu-id="ff496-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="ff496-108">Portanto, as funções canônicas são recomendadas em geral sobre as funções Store- específicas, que estão em um namespace específica do provedor.</span><span class="sxs-lookup"><span data-stu-id="ff496-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="ff496-109">Para obter mais informações, consulte [funções canônicas](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ff496-109">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="ff496-110">O provedor gerenciado cliente do Microsoft SQL fornece um conjunto de funções específicos do provedor.</span><span class="sxs-lookup"><span data-stu-id="ff496-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="ff496-111">Para obter mais informações, consulte [SqlClient para funções de Entity Framework](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ff496-111">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff496-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ff496-112">In This Section</span></span>  
 [<span data-ttu-id="ff496-113">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="ff496-113">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="ff496-114">Resolução de sobrecarga de função</span><span class="sxs-lookup"><span data-stu-id="ff496-114">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="ff496-115">Funções agregadas</span><span class="sxs-lookup"><span data-stu-id="ff496-115">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="ff496-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff496-116">See also</span></span>

- [<span data-ttu-id="ff496-117">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ff496-117">Entity SQL Overview</span></span>](entity-sql-overview.md)

---
title: . (Acesso de membro) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 1db6be632da90eaa7a761bb213e395182ae42347
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250291"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="fe790-103">.</span><span class="sxs-lookup"><span data-stu-id="fe790-103">.</span></span> <span data-ttu-id="fe790-104">(Acesso de membro) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fe790-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="fe790-105">O operador de ponto (.) é [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o operador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="fe790-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="fe790-106">Você usa o operador de acesso de membro para produzir o valor de uma propriedade ou um campo de uma instância do tipo estrutural de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="fe790-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe790-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe790-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="fe790-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="fe790-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fe790-109">Uma instância de um tipo estrutural de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="fe790-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="fe790-110">Uma propriedade ou um campo que pertençam a uma instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="fe790-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe790-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe790-111">Remarks</span></span>  
 <span data-ttu-id="fe790-112">O operador ponto (.) pode ser usado para extrair campos de um registro, semelhante a extrair propriedades de um complexo ou tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="fe790-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="fe790-113">Por exemplo, se n do tipo name for um membro do tipo Person, e p for uma instância do tipo Person, p. n será uma expressão de acesso de membro legal que produz um valor do tipo Name.</span><span class="sxs-lookup"><span data-stu-id="fe790-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="fe790-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe790-114">See also</span></span>

- [<span data-ttu-id="fe790-115">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fe790-115">Entity SQL Reference</span></span>](entity-sql-reference.md)

---
title: . (Acesso de membro) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: e2874e5bff8d8c34f700a81bf52c6729df49aca5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626654"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="ad034-103">.</span><span class="sxs-lookup"><span data-stu-id="ad034-103">.</span></span> <span data-ttu-id="ad034-104">(Acesso de membro) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ad034-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="ad034-105">O operador ponto (.) é o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="ad034-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="ad034-106">Você usa o operador de acesso de membro para produzir o valor de uma propriedade ou um campo de uma instância do tipo estrutural de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="ad034-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad034-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad034-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad034-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="ad034-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ad034-109">Uma instância de um tipo estrutural de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="ad034-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="ad034-110">Uma propriedade ou um campo que pertençam a uma instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="ad034-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad034-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad034-111">Remarks</span></span>  
 <span data-ttu-id="ad034-112">O operador ponto (.) pode ser usado para extrair campos de um registro, semelhante a extrair propriedades de um complexo ou tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="ad034-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="ad034-113">Por exemplo, se n do nome do tipo é um membro do tipo Person e p é uma instância do tipo Person, p.n é uma expressão de acesso de membro legal que gera um valor do nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="ad034-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="ad034-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad034-114">See also</span></span>
- [<span data-ttu-id="ad034-115">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ad034-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

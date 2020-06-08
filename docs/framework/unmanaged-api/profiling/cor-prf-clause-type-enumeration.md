---
title: Enumeração COR_PRF_CLAUSE_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: a308017dc80dd973cbf108ba9df824193775f5ff
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501047"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="99071-102">Enumeração COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="99071-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="99071-103">Indica o tipo de cláusula de exceção que o código acabou de inserir ou deixar.</span><span class="sxs-lookup"><span data-stu-id="99071-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99071-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99071-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="99071-105">Membros</span><span class="sxs-lookup"><span data-stu-id="99071-105">Members</span></span>  
  
|<span data-ttu-id="99071-106">Membro</span><span class="sxs-lookup"><span data-stu-id="99071-106">Member</span></span>|<span data-ttu-id="99071-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="99071-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="99071-108">A cláusula de exceção não é válida.</span><span class="sxs-lookup"><span data-stu-id="99071-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="99071-109">A cláusula de exceção é uma expressão de filtro.</span><span class="sxs-lookup"><span data-stu-id="99071-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="99071-110">A cláusula de exceção é uma `catch` instrução.</span><span class="sxs-lookup"><span data-stu-id="99071-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="99071-111">A cláusula de exceção é uma `finally` instrução.</span><span class="sxs-lookup"><span data-stu-id="99071-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99071-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99071-112">Requirements</span></span>  
 <span data-ttu-id="99071-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99071-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99071-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="99071-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="99071-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99071-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99071-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99071-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99071-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="99071-117">See also</span></span>

- [<span data-ttu-id="99071-118">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="99071-118">Profiling Enumerations</span></span>](profiling-enumerations.md)

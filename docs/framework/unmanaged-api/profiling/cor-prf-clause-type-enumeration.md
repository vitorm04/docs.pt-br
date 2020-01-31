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
ms.openlocfilehash: edf5d61baae28a82aff0d0bd32d1d900085ac375
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867315"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="9a12c-102">Enumeração COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a12c-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="9a12c-103">Indica o tipo de cláusula de exceção que o código acabou de inserir ou deixar.</span><span class="sxs-lookup"><span data-stu-id="9a12c-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a12c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a12c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="9a12c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9a12c-105">Members</span></span>  
  
|<span data-ttu-id="9a12c-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9a12c-106">Member</span></span>|<span data-ttu-id="9a12c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a12c-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="9a12c-108">A cláusula de exceção não é válida.</span><span class="sxs-lookup"><span data-stu-id="9a12c-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="9a12c-109">A cláusula de exceção é uma expressão de filtro.</span><span class="sxs-lookup"><span data-stu-id="9a12c-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="9a12c-110">A cláusula Exception é uma instrução `catch`.</span><span class="sxs-lookup"><span data-stu-id="9a12c-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="9a12c-111">A cláusula Exception é uma instrução `finally`.</span><span class="sxs-lookup"><span data-stu-id="9a12c-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a12c-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9a12c-112">Requirements</span></span>  
 <span data-ttu-id="9a12c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a12c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a12c-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9a12c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a12c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a12c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a12c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a12c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a12c-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="9a12c-117">See also</span></span>

- [<span data-ttu-id="9a12c-118">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="9a12c-118">Profiling Enumerations</span></span>](profiling-enumerations.md)

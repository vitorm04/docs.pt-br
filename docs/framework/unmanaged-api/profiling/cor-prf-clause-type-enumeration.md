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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18197f0c500a205a66bdda8a9401f31d4208ae67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780441"
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="b475f-102">Enumeração COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b475f-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="b475f-103">Indica o tipo de cláusula de exceção que o código acabou de inserir ou deixar.</span><span class="sxs-lookup"><span data-stu-id="b475f-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b475f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b475f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="b475f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b475f-105">Members</span></span>  
  
|<span data-ttu-id="b475f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b475f-106">Member</span></span>|<span data-ttu-id="b475f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b475f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="b475f-108">A cláusula de exceção não é válida.</span><span class="sxs-lookup"><span data-stu-id="b475f-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="b475f-109">A cláusula de exceção é uma expressão de filtro.</span><span class="sxs-lookup"><span data-stu-id="b475f-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="b475f-110">A cláusula de exceção é um `catch` instrução.</span><span class="sxs-lookup"><span data-stu-id="b475f-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="b475f-111">A cláusula de exceção é um `finally` instrução.</span><span class="sxs-lookup"><span data-stu-id="b475f-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b475f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b475f-112">Requirements</span></span>  
 <span data-ttu-id="b475f-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b475f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b475f-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b475f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b475f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b475f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b475f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b475f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b475f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b475f-117">See also</span></span>

- [<span data-ttu-id="b475f-118">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="b475f-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

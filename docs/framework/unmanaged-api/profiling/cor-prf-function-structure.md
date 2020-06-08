---
title: Estrutura COR_PRF_FUNCTION
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 856e01c7934709a17556aa53851204bf6a917de8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500930"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="d5eff-102">Estrutura COR_PRF_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="d5eff-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="d5eff-103">Fornece uma representação única de uma função pela combinação de sua ID com a ID de sua versão recompilada.</span><span class="sxs-lookup"><span data-stu-id="d5eff-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5eff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5eff-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="d5eff-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d5eff-105">Members</span></span>  
  
|<span data-ttu-id="d5eff-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d5eff-106">Member</span></span>|<span data-ttu-id="d5eff-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5eff-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="d5eff-108">A ID da função.</span><span class="sxs-lookup"><span data-stu-id="d5eff-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="d5eff-109">A ID da função recompilada.</span><span class="sxs-lookup"><span data-stu-id="d5eff-109">The ID of the recompiled function.</span></span> <span data-ttu-id="d5eff-110">Um valor de 0 (zero) representa a versão original da função.</span><span class="sxs-lookup"><span data-stu-id="d5eff-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5eff-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5eff-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5eff-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5eff-112">Requirements</span></span>  
 <span data-ttu-id="d5eff-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5eff-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5eff-114">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="d5eff-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d5eff-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5eff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5eff-116">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5eff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5eff-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="d5eff-117">See also</span></span>

- [<span data-ttu-id="d5eff-118">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="d5eff-118">Profiling Structures</span></span>](profiling-structures.md)

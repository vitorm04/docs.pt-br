---
title: Estrutura COR_ACTIVE_FUNCTION
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0400da0cd29d642a1be42be7e2b22213ae54b94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121765"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="72437-102">Estrutura COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="72437-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="72437-103">Contém informações sobre as funções que estão atualmente ativas nos quadros de um thread.</span><span class="sxs-lookup"><span data-stu-id="72437-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="72437-104">Essa estrutura é usada o [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="72437-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72437-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72437-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="72437-106">Membros</span><span class="sxs-lookup"><span data-stu-id="72437-106">Members</span></span>  
  
|<span data-ttu-id="72437-107">Membro</span><span class="sxs-lookup"><span data-stu-id="72437-107">Member</span></span>|<span data-ttu-id="72437-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="72437-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="72437-109">Ponteiro para o proprietário do domínio de aplicativo do `ilOffset` campo.</span><span class="sxs-lookup"><span data-stu-id="72437-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="72437-110">Ponteiro para o proprietário do módulo do `ilOffset` campo.</span><span class="sxs-lookup"><span data-stu-id="72437-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="72437-111">Ponteiro para o proprietário da função do `ilOffset` campo.</span><span class="sxs-lookup"><span data-stu-id="72437-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="72437-112">O deslocamento do MSIL (linguagem intermediária) Microsoft do quadro.</span><span class="sxs-lookup"><span data-stu-id="72437-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="72437-113">Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="72437-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72437-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72437-114">Requirements</span></span>  
 <span data-ttu-id="72437-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72437-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72437-116">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="72437-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="72437-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72437-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="72437-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="72437-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="72437-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72437-119">See also</span></span>

- [<span data-ttu-id="72437-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="72437-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="72437-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="72437-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

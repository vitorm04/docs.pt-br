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
ms.openlocfilehash: cbc272070e9eb6810b34ec1f3fdc9e944c624cd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132376"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="255bf-102">Estrutura COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="255bf-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="255bf-103">Contém informações sobre as funções que estão atualmente ativas nos quadros de um thread.</span><span class="sxs-lookup"><span data-stu-id="255bf-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="255bf-104">Essa estrutura é usada pelo método [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="255bf-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="255bf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="255bf-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="255bf-106">Membros</span><span class="sxs-lookup"><span data-stu-id="255bf-106">Members</span></span>  
  
|<span data-ttu-id="255bf-107">Membro</span><span class="sxs-lookup"><span data-stu-id="255bf-107">Member</span></span>|<span data-ttu-id="255bf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="255bf-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="255bf-109">Ponteiro para o proprietário do domínio de aplicativo do campo `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="255bf-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="255bf-110">Ponteiro para o proprietário do módulo do campo `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="255bf-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="255bf-111">Ponteiro para o proprietário da função do campo `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="255bf-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="255bf-112">O deslocamento da MSIL (Microsoft Intermediate Language) do quadro.</span><span class="sxs-lookup"><span data-stu-id="255bf-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="255bf-113">Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="255bf-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="255bf-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="255bf-114">Requirements</span></span>  
 <span data-ttu-id="255bf-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="255bf-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="255bf-116">**Cabeçalho:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="255bf-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="255bf-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="255bf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="255bf-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="255bf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="255bf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="255bf-119">See also</span></span>

- [<span data-ttu-id="255bf-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="255bf-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="255bf-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="255bf-121">Debugging</span></span>](index.md)

---
title: Método ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 0900ac2ae5bcf2141e720dad6efdf68d4fafaccc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793529"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="1eb3f-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="1eb3f-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="1eb3f-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1eb3f-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eb3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1eb3f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1eb3f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1eb3f-105">Parameters</span></span>  
 <span data-ttu-id="1eb3f-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="1eb3f-106">ppThread</span></span>  
 <span data-ttu-id="1eb3f-107">[out] Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1eb3f-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1eb3f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1eb3f-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1eb3f-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1eb3f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eb3f-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="1eb3f-110">Requirements</span></span>  
 <span data-ttu-id="1eb3f-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eb3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eb3f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1eb3f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1eb3f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1eb3f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eb3f-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eb3f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb3f-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="1eb3f-115">See also</span></span>

- [<span data-ttu-id="1eb3f-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="1eb3f-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="1eb3f-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1eb3f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

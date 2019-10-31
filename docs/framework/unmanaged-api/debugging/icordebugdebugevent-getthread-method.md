---
title: Método ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 66b4abc4bebfbbde2e6a6b25d2bc0e88839a363f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136643"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="1bb97-102">Método ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="1bb97-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="1bb97-103">Obtém o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1bb97-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bb97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bb97-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bb97-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1bb97-105">Parameters</span></span>  
 <span data-ttu-id="1bb97-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="1bb97-106">ppThread</span></span>  
 <span data-ttu-id="1bb97-107">fora Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread no qual o evento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="1bb97-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bb97-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bb97-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bb97-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1bb97-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bb97-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1bb97-110">Requirements</span></span>  
 <span data-ttu-id="1bb97-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bb97-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bb97-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bb97-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bb97-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bb97-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bb97-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bb97-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb97-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bb97-115">See also</span></span>

- [<span data-ttu-id="1bb97-116">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="1bb97-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="1bb97-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1bb97-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

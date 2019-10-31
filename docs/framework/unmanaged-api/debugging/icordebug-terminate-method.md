---
title: Método ICorDebug::Terminate
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 78838e9002cb3f5263395af9de255c54de47b6ae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134024"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="633b9-102">Método ICorDebug::Terminate</span><span class="sxs-lookup"><span data-stu-id="633b9-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="633b9-103">Encerra o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="633b9-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="633b9-104">`Terminate` não deve ser chamado até que um retorno de chamada [ICorDebugManagedCallback:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) tenha sido recebido para todos os processos sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="633b9-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="633b9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="633b9-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="633b9-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="633b9-106">Remarks</span></span>  
 <span data-ttu-id="633b9-107">`Terminate` deve ser chamado quando o objeto de `ICorDebug` não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="633b9-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="633b9-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="633b9-108">Requirements</span></span>  
 <span data-ttu-id="633b9-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="633b9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="633b9-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="633b9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="633b9-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="633b9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="633b9-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="633b9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="633b9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="633b9-113">See also</span></span>

- [<span data-ttu-id="633b9-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="633b9-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

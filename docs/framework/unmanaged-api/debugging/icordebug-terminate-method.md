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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c2b590e7402bf29ffeb5bd14fc383edae41a04e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="4d368-102">Método ICorDebug::Terminate</span><span class="sxs-lookup"><span data-stu-id="4d368-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="4d368-103">Encerra o `ICorDebug` objeto.</span><span class="sxs-lookup"><span data-stu-id="4d368-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d368-104">`Terminate` não deve ser chamado até um [: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) retorno de chamada foi recebido para todos os processos que está sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="4d368-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d368-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d368-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4d368-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d368-106">Remarks</span></span>  
 <span data-ttu-id="4d368-107">`Terminate` deve ser chamado quando o `ICorDebug` objeto não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="4d368-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d368-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d368-108">Requirements</span></span>  
 <span data-ttu-id="4d368-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d368-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d368-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d368-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d368-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d368-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d368-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d368-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d368-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d368-113">See Also</span></span>  
 [<span data-ttu-id="4d368-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="4d368-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

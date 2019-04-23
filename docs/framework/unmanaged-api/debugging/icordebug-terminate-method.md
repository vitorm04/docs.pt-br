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
ms.openlocfilehash: 321298ce942b35d11a861c87cdf6b8714179ea97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080824"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="82240-102">Método ICorDebug::Terminate</span><span class="sxs-lookup"><span data-stu-id="82240-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="82240-103">Encerra o `ICorDebug` objeto.</span><span class="sxs-lookup"><span data-stu-id="82240-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82240-104">`Terminate` não deve ser chamado até que um [icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) retorno de chamada foi recebido para todos os processos que estão sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="82240-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82240-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82240-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="82240-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="82240-106">Remarks</span></span>  
 <span data-ttu-id="82240-107">`Terminate` deve ser chamado quando o `ICorDebug` objeto não for mais necessário.</span><span class="sxs-lookup"><span data-stu-id="82240-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82240-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82240-108">Requirements</span></span>  
 <span data-ttu-id="82240-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82240-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82240-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82240-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82240-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82240-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82240-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82240-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82240-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82240-113">See also</span></span>

- [<span data-ttu-id="82240-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="82240-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

---
title: "Método ICorDebugMutableDataTarget::ContinueStatusChanged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ba8fe9b0d4a09bdfe3d3e6459f16bf041dc396a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="f516b-102">Método ICorDebugMutableDataTarget::ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="f516b-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="f516b-103">Altera o status de continuação para o evento de depuração pendentes no thread especificado.</span><span class="sxs-lookup"><span data-stu-id="f516b-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f516b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f516b-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f516b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f516b-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="f516b-106">O identificador de thread definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f516b-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="f516b-107">Um[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)solicitado de valor que representa o novo status de continuação.</span><span class="sxs-lookup"><span data-stu-id="f516b-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f516b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f516b-108">Remarks</span></span>  
 <span data-ttu-id="f516b-109">As chamadas do depurador de `ContinueStatusChanged` método quando ele chama um método ICorDebug que requer que o evento de depuração atual deve ser tratado de forma que é potencialmente diferente da maneira em que ele normalmente seria manipulado.</span><span class="sxs-lookup"><span data-stu-id="f516b-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="f516b-110">Por exemplo, se há uma exceção pendente e o depurador solicita uma operação que cancelará a exceção (como [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou `FuncEval`), essa API é usada para solicitar que a exceção seja cancelada.</span><span class="sxs-lookup"><span data-stu-id="f516b-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f516b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f516b-111">Requirements</span></span>  
 <span data-ttu-id="f516b-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f516b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f516b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f516b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f516b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f516b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f516b-115">**Versões do .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f516b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f516b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f516b-116">See Also</span></span>  
 [<span data-ttu-id="f516b-117">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="f516b-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="f516b-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f516b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

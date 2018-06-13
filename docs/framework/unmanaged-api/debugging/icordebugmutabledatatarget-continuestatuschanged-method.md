---
title: Método ICorDebugMutableDataTarget::ContinueStatusChanged
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb07c519743c41a7a31994e42d2fdc5220e5e2ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418204"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="c6aae-102">Método ICorDebugMutableDataTarget::ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="c6aae-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="c6aae-103">Altera o status de continuação para o evento de depuração pendentes no thread especificado.</span><span class="sxs-lookup"><span data-stu-id="c6aae-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6aae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6aae-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6aae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6aae-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="c6aae-106">O identificador de thread definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c6aae-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="c6aae-107">Um[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)solicitado de valor que representa o novo status de continuação.</span><span class="sxs-lookup"><span data-stu-id="c6aae-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6aae-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6aae-108">Remarks</span></span>  
 <span data-ttu-id="c6aae-109">As chamadas do depurador de `ContinueStatusChanged` método quando ele chama um método ICorDebug que requer que o evento de depuração atual deve ser tratado de forma que é potencialmente diferente da maneira em que ele normalmente seria manipulado.</span><span class="sxs-lookup"><span data-stu-id="c6aae-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="c6aae-110">Por exemplo, se há uma exceção pendente e o depurador solicita uma operação que cancelará a exceção (como [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou `FuncEval`), essa API é usada para solicitar que a exceção seja cancelada.</span><span class="sxs-lookup"><span data-stu-id="c6aae-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6aae-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6aae-111">Requirements</span></span>  
 <span data-ttu-id="c6aae-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6aae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6aae-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6aae-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6aae-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6aae-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6aae-115">**Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6aae-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6aae-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6aae-116">See Also</span></span>  
 [<span data-ttu-id="c6aae-117">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="c6aae-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="c6aae-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c6aae-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

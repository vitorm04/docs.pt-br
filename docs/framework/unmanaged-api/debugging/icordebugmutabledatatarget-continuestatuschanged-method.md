---
title: Método ICorDebugMutableDataTarget::ContinueStatusChanged
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52b5c63f35732655834768eb5b914406203d423c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135610"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="8899c-102">Método ICorDebugMutableDataTarget::ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="8899c-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="8899c-103">Altera o status de continuação para o evento de depuração pendente no thread especificado.</span><span class="sxs-lookup"><span data-stu-id="8899c-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8899c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8899c-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8899c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8899c-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="8899c-106">O identificador de thread definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="8899c-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="8899c-107">Um valor [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o novo status de continuação solicitado.</span><span class="sxs-lookup"><span data-stu-id="8899c-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8899c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8899c-108">Remarks</span></span>  
 <span data-ttu-id="8899c-109">O depurador chama o método `ContinueStatusChanged` quando ele chama um método ICorDebug que exige que o evento de depuração atual seja tratado de modo potencialmente diferente da maneira como ele normalmente seria tratado.</span><span class="sxs-lookup"><span data-stu-id="8899c-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="8899c-110">Por exemplo, se houver uma exceção pendente e o depurador solicitar uma operação que cancelaria a exceção (como [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou `FuncEval`), essa API será usada para solicitar que a exceção seja cancelada.</span><span class="sxs-lookup"><span data-stu-id="8899c-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8899c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8899c-111">Requirements</span></span>  
 <span data-ttu-id="8899c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8899c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8899c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8899c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8899c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8899c-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8899c-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8899c-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8899c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8899c-116">See also</span></span>

- [<span data-ttu-id="8899c-117">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="8899c-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="8899c-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8899c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

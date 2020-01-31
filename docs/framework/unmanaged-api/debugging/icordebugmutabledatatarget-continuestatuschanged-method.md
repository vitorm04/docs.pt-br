---
title: Método ICorDebugMutableDataTarget::ContinueStatusChanged
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: c918bb60fba5bc1ec3f0f7c58b103d05a3c7ddfd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792870"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="71088-102">Método ICorDebugMutableDataTarget::ContinueStatusChanged</span><span class="sxs-lookup"><span data-stu-id="71088-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="71088-103">Altera o status de continuação para o evento de depuração pendente no thread especificado.</span><span class="sxs-lookup"><span data-stu-id="71088-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71088-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71088-104">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71088-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="71088-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="71088-106">O identificador de thread definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="71088-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="71088-107">Um valor [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o novo status de continuação solicitado.</span><span class="sxs-lookup"><span data-stu-id="71088-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71088-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="71088-108">Remarks</span></span>  
 <span data-ttu-id="71088-109">O depurador chama o método `ContinueStatusChanged` quando ele chama um método ICorDebug que exige que o evento de depuração atual seja tratado de modo potencialmente diferente da maneira como ele normalmente seria tratado.</span><span class="sxs-lookup"><span data-stu-id="71088-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="71088-110">Por exemplo, se houver uma exceção pendente e o depurador solicitar uma operação que cancelaria a exceção (como [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) ou `FuncEval`), essa API será usada para solicitar que a exceção seja cancelada.</span><span class="sxs-lookup"><span data-stu-id="71088-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71088-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="71088-111">Requirements</span></span>  
 <span data-ttu-id="71088-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71088-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71088-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71088-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71088-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71088-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71088-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71088-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71088-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="71088-116">See also</span></span>

- [<span data-ttu-id="71088-117">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="71088-117">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="71088-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="71088-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

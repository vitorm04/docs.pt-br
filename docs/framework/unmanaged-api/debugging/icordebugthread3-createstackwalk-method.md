---
title: Método ICorDebugThread3::CreateStackWalk
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7969d8482970b13951938203262f6ce8f9bf574a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229297"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="26187-102">Método ICorDebugThread3::CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="26187-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="26187-103">Cria uma [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja pilha que você deseja de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="26187-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26187-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26187-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26187-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26187-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="26187-106">[out] Um ponteiro para o endereço do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja pilha que você deseja de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="26187-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26187-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="26187-107">Return Value</span></span>  
 <span data-ttu-id="26187-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="26187-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="26187-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26187-109">HRESULT</span></span>|<span data-ttu-id="26187-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="26187-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26187-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="26187-111">S_OK</span></span>|<span data-ttu-id="26187-112">O `ICorDebugStackWalk` objeto foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="26187-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="26187-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26187-113">E_FAIL</span></span>|<span data-ttu-id="26187-114">O `ICorDebugStackWalk` objeto não foi criado.</span><span class="sxs-lookup"><span data-stu-id="26187-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="26187-115">Exceções</span><span class="sxs-lookup"><span data-stu-id="26187-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26187-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="26187-116">Remarks</span></span>  
 <span data-ttu-id="26187-117">Se o `CreateStackWalk` método for bem-sucedido, retornado `ICorDebugStackWalk` contexto de objeto é definido como o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="26187-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26187-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26187-118">Requirements</span></span>  
 <span data-ttu-id="26187-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26187-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26187-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26187-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26187-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26187-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26187-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26187-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26187-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26187-123">See also</span></span>

- [<span data-ttu-id="26187-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="26187-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="26187-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="26187-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

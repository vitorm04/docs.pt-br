---
title: "Método ICorDebugThread3::CreateStackWalk"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.CreateStackWalk Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 022b60b50c5e38a776b9076fd4faa62a3c373b06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="51ccb-102">Método ICorDebugThread3::CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="51ccb-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="51ccb-103">Cria um [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja deseja desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="51ccb-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ccb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51ccb-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51ccb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51ccb-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="51ccb-106">[out] Um ponteiro para o endereço do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja deseja desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="51ccb-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51ccb-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="51ccb-107">Return Value</span></span>  
 <span data-ttu-id="51ccb-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="51ccb-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="51ccb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51ccb-109">HRESULT</span></span>|<span data-ttu-id="51ccb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="51ccb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51ccb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="51ccb-111">S_OK</span></span>|<span data-ttu-id="51ccb-112">O `ICorDebugStackWalk` objeto foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="51ccb-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="51ccb-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51ccb-113">E_FAIL</span></span>|<span data-ttu-id="51ccb-114">O `ICorDebugStackWalk` objeto não foi criado.</span><span class="sxs-lookup"><span data-stu-id="51ccb-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="51ccb-115">Exceções</span><span class="sxs-lookup"><span data-stu-id="51ccb-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51ccb-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="51ccb-116">Remarks</span></span>  
 <span data-ttu-id="51ccb-117">Se o `CreateStackWalk` método for bem-sucedido, retornado `ICorDebugStackWalk` contexto do objeto é definido como o contexto do thread atual.</span><span class="sxs-lookup"><span data-stu-id="51ccb-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51ccb-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51ccb-118">Requirements</span></span>  
 <span data-ttu-id="51ccb-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51ccb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51ccb-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51ccb-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51ccb-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51ccb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51ccb-122">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51ccb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ccb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51ccb-123">See Also</span></span>  
 [<span data-ttu-id="51ccb-124">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="51ccb-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="51ccb-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="51ccb-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

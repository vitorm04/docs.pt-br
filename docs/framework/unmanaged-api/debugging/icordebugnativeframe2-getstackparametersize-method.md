---
title: "Método ICorDebugNativeFrame2::GetStackParameterSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.GetStackParameterSize Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa7e67c252f2ece16c072e22d0333e085fbc4f65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="17dfd-102">Método ICorDebugNativeFrame2::GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="17dfd-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="17dfd-103">Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.</span><span class="sxs-lookup"><span data-stu-id="17dfd-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17dfd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17dfd-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17dfd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17dfd-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="17dfd-106">[out] Um ponteiro para o tamanho cumulativo de parâmetros na pilha.</span><span class="sxs-lookup"><span data-stu-id="17dfd-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17dfd-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="17dfd-107">Return Value</span></span>  
 <span data-ttu-id="17dfd-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="17dfd-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="17dfd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17dfd-109">HRESULT</span></span>|<span data-ttu-id="17dfd-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="17dfd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17dfd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="17dfd-111">S_OK</span></span>|<span data-ttu-id="17dfd-112">O tamanho da pilha foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="17dfd-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="17dfd-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="17dfd-113">S_FALSE</span></span>|<span data-ttu-id="17dfd-114">`GetStackParameterSize`foi chamado em uma plataforma x86 não.</span><span class="sxs-lookup"><span data-stu-id="17dfd-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="17dfd-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17dfd-115">E_FAIL</span></span>|<span data-ttu-id="17dfd-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="17dfd-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="17dfd-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="17dfd-117">E_INVALIDARG</span></span>|<span data-ttu-id="17dfd-118">`pSize`É `null`.</span><span class="sxs-lookup"><span data-stu-id="17dfd-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="17dfd-119">Exceções</span><span class="sxs-lookup"><span data-stu-id="17dfd-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17dfd-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="17dfd-120">Remarks</span></span>  
 <span data-ttu-id="17dfd-121">O [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) métodos não ajustar o ponteiro de pilha para os parâmetros que são enviados por push na pilha.</span><span class="sxs-lookup"><span data-stu-id="17dfd-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="17dfd-122">Em vez disso, você pode usar o valor retornado por `GetStackParameterSize` para ajustar o ponteiro de pilha para propagar um unwinder nativo, ajustá-lo para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17dfd-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17dfd-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17dfd-123">Requirements</span></span>  
 <span data-ttu-id="17dfd-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17dfd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17dfd-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17dfd-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17dfd-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17dfd-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17dfd-127">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17dfd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17dfd-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17dfd-128">See Also</span></span>  
 [<span data-ttu-id="17dfd-129">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="17dfd-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="17dfd-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="17dfd-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="17dfd-131">Depuração</span><span class="sxs-lookup"><span data-stu-id="17dfd-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

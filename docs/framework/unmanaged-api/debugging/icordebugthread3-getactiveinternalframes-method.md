---
title: "Método ICorDebugThread3::GetActiveInternalFrames"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.GetActiveInternalFrames Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9b94827ac49c69c5e72c2e300a80914774cc498
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="7abdd-102">Método ICorDebugThread3::GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="7abdd-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="7abdd-103">Retorna uma matriz de quadros internos ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objetos) na pilha.</span><span class="sxs-lookup"><span data-stu-id="7abdd-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abdd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7abdd-104">Syntax</span></span>  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7abdd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7abdd-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="7abdd-106">[in] O número de quadros internos esperado em `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="7abdd-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="7abdd-107">[out] Um ponteiro para um `ULONG32` que contém o número de quadros internos na pilha.</span><span class="sxs-lookup"><span data-stu-id="7abdd-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="7abdd-108">[out no] Um ponteiro para o endereço de uma matriz de quadros internos na pilha.</span><span class="sxs-lookup"><span data-stu-id="7abdd-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7abdd-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7abdd-109">Return Value</span></span>  
 <span data-ttu-id="7abdd-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="7abdd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7abdd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7abdd-111">HRESULT</span></span>|<span data-ttu-id="7abdd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7abdd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7abdd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7abdd-113">S_OK</span></span>|<span data-ttu-id="7abdd-114">O [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objeto foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7abdd-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="7abdd-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7abdd-115">E_INVALIDARG</span></span>|<span data-ttu-id="7abdd-116">`cInternalFrames`não é zero e `ppInternalFrames` é `null`, ou `pcInternalFrames` é `null`.</span><span class="sxs-lookup"><span data-stu-id="7abdd-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="7abdd-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="7abdd-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="7abdd-118">`ppInternalFrames`é menor do que a contagem de quadros internos.</span><span class="sxs-lookup"><span data-stu-id="7abdd-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="7abdd-119">Exceções</span><span class="sxs-lookup"><span data-stu-id="7abdd-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7abdd-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="7abdd-120">Remarks</span></span>  
 <span data-ttu-id="7abdd-121">Quadros internos são estruturas de dados inseridas na pilha pelo tempo de execução para armazenar dados temporários.</span><span class="sxs-lookup"><span data-stu-id="7abdd-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="7abdd-122">Quando você chama primeiro `GetActiveInternalFrames`, você deve definir o `cInternalFrames` parâmetro como 0 (zero) e o `ppInternalFrames` parâmetro como null.</span><span class="sxs-lookup"><span data-stu-id="7abdd-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="7abdd-123">Quando `GetActiveInternalFrames` retorna primeiro, `pcInternalFrames` contém a contagem de quadros na pilha internas.</span><span class="sxs-lookup"><span data-stu-id="7abdd-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="7abdd-124">`GetActiveInternalFrames`deve ser chamado pela segunda vez.</span><span class="sxs-lookup"><span data-stu-id="7abdd-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="7abdd-125">Você deve passar a contagem adequada (`pcInternalFrames`) no `cInternalFrames` parâmetro, e especifique um ponteiro para uma matriz de tamanho apropriado no `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="7abdd-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="7abdd-126">Use o [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) quadros de pilha do método de retorno real.</span><span class="sxs-lookup"><span data-stu-id="7abdd-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abdd-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7abdd-127">Requirements</span></span>  
 <span data-ttu-id="7abdd-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7abdd-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abdd-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7abdd-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7abdd-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7abdd-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7abdd-131">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7abdd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abdd-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7abdd-132">See Also</span></span>  
 [<span data-ttu-id="7abdd-133">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="7abdd-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7abdd-134">Depuração</span><span class="sxs-lookup"><span data-stu-id="7abdd-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

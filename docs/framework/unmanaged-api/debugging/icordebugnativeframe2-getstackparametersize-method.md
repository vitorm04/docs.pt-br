---
title: Método ICorDebugNativeFrame2::GetStackParameterSize
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47968d7550c3d16d201680caab705c0d7c85c784
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200136"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="1de79-102">Método ICorDebugNativeFrame2::GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="1de79-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="1de79-103">Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.</span><span class="sxs-lookup"><span data-stu-id="1de79-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1de79-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1de79-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1de79-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1de79-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="1de79-106">[out] Um ponteiro para o tamanho cumulativo dos parâmetros na pilha.</span><span class="sxs-lookup"><span data-stu-id="1de79-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1de79-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1de79-107">Return Value</span></span>  
 <span data-ttu-id="1de79-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="1de79-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1de79-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1de79-109">HRESULT</span></span>|<span data-ttu-id="1de79-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="1de79-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1de79-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1de79-111">S_OK</span></span>|<span data-ttu-id="1de79-112">O tamanho da pilha foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1de79-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="1de79-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1de79-113">S_FALSE</span></span>|`GetStackParameterSize` <span data-ttu-id="1de79-114">foi chamado em uma plataforma não x86.</span><span class="sxs-lookup"><span data-stu-id="1de79-114">was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="1de79-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1de79-115">E_FAIL</span></span>|`The size of the parameters could not be returned`<span data-ttu-id="1de79-116">.</span><span class="sxs-lookup"><span data-stu-id="1de79-116">.</span></span>|  
|<span data-ttu-id="1de79-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1de79-117">E_INVALIDARG</span></span>|`pSize` <span data-ttu-id="1de79-118">Is `null`.</span><span class="sxs-lookup"><span data-stu-id="1de79-118">Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1de79-119">Exceções</span><span class="sxs-lookup"><span data-stu-id="1de79-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1de79-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="1de79-120">Remarks</span></span>  
 <span data-ttu-id="1de79-121">O [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) métodos não ajustar o ponteiro de pilha para os parâmetros que são enviados por push na pilha.</span><span class="sxs-lookup"><span data-stu-id="1de79-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="1de79-122">Em vez disso, você pode usar o valor retornado por `GetStackParameterSize` para ajustar o ponteiro de pilha para propagar um desenrolador nativo, ajustá-lo para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1de79-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1de79-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1de79-123">Requirements</span></span>  
 <span data-ttu-id="1de79-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1de79-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1de79-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1de79-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1de79-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1de79-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1de79-127">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1de79-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1de79-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1de79-128">See also</span></span>

- [<span data-ttu-id="1de79-129">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="1de79-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="1de79-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1de79-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1de79-131">Depuração</span><span class="sxs-lookup"><span data-stu-id="1de79-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

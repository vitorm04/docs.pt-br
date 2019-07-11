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
ms.openlocfilehash: 8a5f0f767a7057064e285bf6ac9dcefc86eb9d79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757210"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="44283-102">Método ICorDebugNativeFrame2::GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="44283-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="44283-103">Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.</span><span class="sxs-lookup"><span data-stu-id="44283-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44283-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44283-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="44283-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44283-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="44283-106">[out] Um ponteiro para o tamanho cumulativo dos parâmetros na pilha.</span><span class="sxs-lookup"><span data-stu-id="44283-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44283-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="44283-107">Return Value</span></span>  
 <span data-ttu-id="44283-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="44283-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44283-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44283-109">HRESULT</span></span>|<span data-ttu-id="44283-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="44283-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44283-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="44283-111">S_OK</span></span>|<span data-ttu-id="44283-112">O tamanho da pilha foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="44283-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="44283-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="44283-113">S_FALSE</span></span>|<span data-ttu-id="44283-114">`GetStackParameterSize` foi chamado em uma plataforma não x86.</span><span class="sxs-lookup"><span data-stu-id="44283-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="44283-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44283-115">E_FAIL</span></span>|<span data-ttu-id="44283-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="44283-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="44283-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="44283-117">E_INVALIDARG</span></span>|<span data-ttu-id="44283-118">`pSize` é `null`.</span><span class="sxs-lookup"><span data-stu-id="44283-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="44283-119">Exceções</span><span class="sxs-lookup"><span data-stu-id="44283-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44283-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="44283-120">Remarks</span></span>  
 <span data-ttu-id="44283-121">O [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) métodos não ajustar o ponteiro de pilha para os parâmetros que são enviados por push na pilha.</span><span class="sxs-lookup"><span data-stu-id="44283-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="44283-122">Em vez disso, você pode usar o valor retornado por `GetStackParameterSize` para ajustar o ponteiro de pilha para propagar um desenrolador nativo, ajustá-lo para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="44283-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44283-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44283-123">Requirements</span></span>  
 <span data-ttu-id="44283-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44283-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44283-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44283-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44283-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44283-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44283-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44283-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44283-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44283-128">See also</span></span>

- [<span data-ttu-id="44283-129">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="44283-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="44283-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="44283-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="44283-131">Depuração</span><span class="sxs-lookup"><span data-stu-id="44283-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

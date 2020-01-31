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
ms.openlocfilehash: ca742ba9e89e1d189cfa38dead314df0d8b4e9d1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792770"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="ac796-102">Método ICorDebugNativeFrame2::GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="ac796-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="ac796-103">Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.</span><span class="sxs-lookup"><span data-stu-id="ac796-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac796-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac796-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac796-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac796-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="ac796-106">fora Um ponteiro para o tamanho cumulativo dos parâmetros na pilha.</span><span class="sxs-lookup"><span data-stu-id="ac796-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac796-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac796-107">Return Value</span></span>  
 <span data-ttu-id="ac796-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="ac796-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ac796-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac796-109">HRESULT</span></span>|<span data-ttu-id="ac796-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac796-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac796-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac796-111">S_OK</span></span>|<span data-ttu-id="ac796-112">O tamanho da pilha foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac796-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="ac796-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ac796-113">S_FALSE</span></span>|<span data-ttu-id="ac796-114">`GetStackParameterSize` foi chamado em uma plataforma não x86.</span><span class="sxs-lookup"><span data-stu-id="ac796-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="ac796-115">{1&gt;E_FAIL&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ac796-115">E_FAIL</span></span>|<span data-ttu-id="ac796-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="ac796-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="ac796-117">{1&gt;E_INVALIDARG&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ac796-117">E_INVALIDARG</span></span>|<span data-ttu-id="ac796-118">`pSize` `null`.</span><span class="sxs-lookup"><span data-stu-id="ac796-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ac796-119">Exceções</span><span class="sxs-lookup"><span data-stu-id="ac796-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac796-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac796-120">Remarks</span></span>  
 <span data-ttu-id="ac796-121">Os métodos [ICorDebugStackWalk](icordebugstackwalk-interface.md) não ajustam o ponteiro de pilha para parâmetros que são enviados por push na pilha.</span><span class="sxs-lookup"><span data-stu-id="ac796-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="ac796-122">Em vez disso, você pode usar o valor retornado por `GetStackParameterSize` para ajustar o ponteiro de pilha para propagar um desenrolador nativo, que ajusta os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ac796-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac796-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ac796-123">Requirements</span></span>  
 <span data-ttu-id="ac796-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac796-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac796-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac796-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac796-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac796-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac796-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac796-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac796-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="ac796-128">See also</span></span>

- [<span data-ttu-id="ac796-129">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="ac796-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="ac796-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ac796-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ac796-131">Depuração</span><span class="sxs-lookup"><span data-stu-id="ac796-131">Debugging</span></span>](index.md)

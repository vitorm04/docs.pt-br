---
title: Método ICorDebugInternalFrame2::IsCloserToLeaf
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: 8b9ec94184945c19b77247175e51bd5e8dc1ceee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122661"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="3fdfe-102">Método ICorDebugInternalFrame2::IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="3fdfe-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="3fdfe-103">Verifica se o quadro interno `this` está mais próximo da folha do que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="3fdfe-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fdfe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fdfe-104">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fdfe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fdfe-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="3fdfe-106">no Um ponteiro para a comparação `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="3fdfe-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="3fdfe-107">[fora] `true` se o quadro interno `this` está mais próximo da folha do que o quadro especificado por `pFrameToCompare`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="3fdfe-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fdfe-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3fdfe-108">Return Value</span></span>  
 <span data-ttu-id="3fdfe-109">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="3fdfe-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3fdfe-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3fdfe-110">HRESULT</span></span>|<span data-ttu-id="3fdfe-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="3fdfe-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3fdfe-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3fdfe-112">S_OK</span></span>|<span data-ttu-id="3fdfe-113">A comparação foi executada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3fdfe-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="3fdfe-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3fdfe-114">E_FAIL</span></span>|<span data-ttu-id="3fdfe-115">Não foi possível executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="3fdfe-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="3fdfe-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3fdfe-116">E_INVALIDARG</span></span>|<span data-ttu-id="3fdfe-117">`pFrameToCompare` ou `pIsCloser` é nulo.</span><span class="sxs-lookup"><span data-stu-id="3fdfe-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fdfe-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fdfe-118">Remarks</span></span>  
 <span data-ttu-id="3fdfe-119">`IsCloserToLeaf` pode ser usado para implementar uma política para intercalar quadros internos com outros quadros na pilha.</span><span class="sxs-lookup"><span data-stu-id="3fdfe-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fdfe-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fdfe-120">Requirements</span></span>  
 <span data-ttu-id="3fdfe-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fdfe-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fdfe-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fdfe-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fdfe-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fdfe-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fdfe-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fdfe-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fdfe-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fdfe-125">See also</span></span>

- [<span data-ttu-id="3fdfe-126">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="3fdfe-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="3fdfe-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3fdfe-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3fdfe-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="3fdfe-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

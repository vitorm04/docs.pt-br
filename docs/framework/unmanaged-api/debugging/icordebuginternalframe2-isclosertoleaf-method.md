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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a5dca321470b3fda8490ca5ae809045d724150
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552158"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="504a9-102">Método ICorDebugInternalFrame2::IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="504a9-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="504a9-103">Verifica se o `this` quadro interno está mais próximo da folha que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="504a9-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="504a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="504a9-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="504a9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="504a9-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="504a9-106">[in] Um ponteiro para a comparação `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="504a9-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="504a9-107">[out] `true` se o `this` quadro interno está mais próximo da folha que o quadro especificado por `pFrameToCompare`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="504a9-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="504a9-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="504a9-108">Return Value</span></span>  
 <span data-ttu-id="504a9-109">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="504a9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="504a9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="504a9-110">HRESULT</span></span>|<span data-ttu-id="504a9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="504a9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="504a9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="504a9-112">S_OK</span></span>|<span data-ttu-id="504a9-113">A comparação foi realizada com êxito.</span><span class="sxs-lookup"><span data-stu-id="504a9-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="504a9-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="504a9-114">E_FAIL</span></span>|<span data-ttu-id="504a9-115">A comparação não pôde ser executada.</span><span class="sxs-lookup"><span data-stu-id="504a9-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="504a9-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="504a9-116">E_INVALIDARG</span></span>|<span data-ttu-id="504a9-117">`pFrameToCompare` ou `pIsCloser` é nulo.</span><span class="sxs-lookup"><span data-stu-id="504a9-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="504a9-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="504a9-118">Remarks</span></span>  
 <span data-ttu-id="504a9-119">`IsCloserToLeaf` pode ser usado para implementar uma política de intercalação quadros internos com outros quadros na pilha.</span><span class="sxs-lookup"><span data-stu-id="504a9-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="504a9-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="504a9-120">Requirements</span></span>  
 <span data-ttu-id="504a9-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="504a9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="504a9-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="504a9-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="504a9-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="504a9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="504a9-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="504a9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="504a9-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="504a9-125">See also</span></span>
- [<span data-ttu-id="504a9-126">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="504a9-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="504a9-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="504a9-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="504a9-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="504a9-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

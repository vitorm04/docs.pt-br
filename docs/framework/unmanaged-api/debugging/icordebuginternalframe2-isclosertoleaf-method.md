---
title: "Método ICorDebugInternalFrame2::IsCloserToLeaf"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60e63800ade5fb0d4a222d80ebfe43c3d84c2815
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="91a9a-102">Método ICorDebugInternalFrame2::IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="91a9a-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="91a9a-103">Verifica se o `this` quadro interno é mais próximo a folha que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="91a9a-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a9a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91a9a-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91a9a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91a9a-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="91a9a-106">[in] Um ponteiro para a comparação `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="91a9a-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="91a9a-107">[out] `true` se o `this` quadro interno é mais próximo a folha que o quadro especificado por `pFrameToCompare`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="91a9a-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91a9a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="91a9a-108">Return Value</span></span>  
 <span data-ttu-id="91a9a-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="91a9a-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="91a9a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91a9a-110">HRESULT</span></span>|<span data-ttu-id="91a9a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="91a9a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91a9a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="91a9a-112">S_OK</span></span>|<span data-ttu-id="91a9a-113">A comparação foi executada com êxito.</span><span class="sxs-lookup"><span data-stu-id="91a9a-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="91a9a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91a9a-114">E_FAIL</span></span>|<span data-ttu-id="91a9a-115">Não foi possível executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="91a9a-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="91a9a-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="91a9a-116">E_INVALIDARG</span></span>|<span data-ttu-id="91a9a-117">`pFrameToCompare` ou `pIsCloser` é nulo.</span><span class="sxs-lookup"><span data-stu-id="91a9a-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91a9a-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="91a9a-118">Remarks</span></span>  
 <span data-ttu-id="91a9a-119">`IsCloserToLeaf`pode ser usado para implementar uma política para a intercalação de quadros internos com outros quadros na pilha.</span><span class="sxs-lookup"><span data-stu-id="91a9a-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a9a-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91a9a-120">Requirements</span></span>  
 <span data-ttu-id="91a9a-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91a9a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91a9a-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91a9a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91a9a-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91a9a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91a9a-124">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91a9a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a9a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91a9a-125">See Also</span></span>  
 [<span data-ttu-id="91a9a-126">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="91a9a-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="91a9a-127">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="91a9a-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="91a9a-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="91a9a-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

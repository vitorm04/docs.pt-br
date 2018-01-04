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
ms.workload: dotnet
ms.openlocfilehash: 7b6b769c25e0cd706eb57965b73d0fcfdcf9b9ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="fe394-102">Método ICorDebugInternalFrame2::IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="fe394-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="fe394-103">Verifica se o `this` quadro interno é mais próximo a folha que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="fe394-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe394-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe394-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe394-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe394-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="fe394-106">[in] Um ponteiro para a comparação `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="fe394-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="fe394-107">[out] `true` se o `this` quadro interno é mais próximo a folha que o quadro especificado por `pFrameToCompare`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="fe394-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe394-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fe394-108">Return Value</span></span>  
 <span data-ttu-id="fe394-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="fe394-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fe394-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe394-110">HRESULT</span></span>|<span data-ttu-id="fe394-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe394-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe394-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe394-112">S_OK</span></span>|<span data-ttu-id="fe394-113">A comparação foi executada com êxito.</span><span class="sxs-lookup"><span data-stu-id="fe394-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="fe394-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe394-114">E_FAIL</span></span>|<span data-ttu-id="fe394-115">Não foi possível executar a comparação.</span><span class="sxs-lookup"><span data-stu-id="fe394-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="fe394-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fe394-116">E_INVALIDARG</span></span>|<span data-ttu-id="fe394-117">`pFrameToCompare` ou `pIsCloser` é nulo.</span><span class="sxs-lookup"><span data-stu-id="fe394-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe394-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe394-118">Remarks</span></span>  
 <span data-ttu-id="fe394-119">`IsCloserToLeaf`pode ser usado para implementar uma política para a intercalação de quadros internos com outros quadros na pilha.</span><span class="sxs-lookup"><span data-stu-id="fe394-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe394-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe394-120">Requirements</span></span>  
 <span data-ttu-id="fe394-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe394-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe394-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe394-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe394-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe394-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe394-124">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe394-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe394-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe394-125">See Also</span></span>  
 [<span data-ttu-id="fe394-126">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="fe394-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="fe394-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fe394-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fe394-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="fe394-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

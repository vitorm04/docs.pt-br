---
title: "Método ICorDebugNativeFrame2::IsMatchingParentFrame"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e261f4cb43843ec61ec6cbd1609e6967a4a38a82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="8f356-102">Método ICorDebugNativeFrame2::IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="8f356-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="8f356-103">Determina se o intervalo especificado é o pai do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="8f356-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f356-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f356-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f356-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f356-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="8f356-106">[in] Um ponteiro para o objeto de quadro que você deseja avaliar o status de pai.</span><span class="sxs-lookup"><span data-stu-id="8f356-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="8f356-107">[out] `true` se `pPotentialParentFrame` é pai do quadro atual; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="8f356-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f356-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8f356-108">Return Value</span></span>  
 <span data-ttu-id="8f356-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="8f356-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8f356-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f356-110">HRESULT</span></span>|<span data-ttu-id="8f356-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f356-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f356-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f356-112">S_OK</span></span>|<span data-ttu-id="8f356-113">O status do pai foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8f356-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="8f356-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f356-114">E_FAIL</span></span>|<span data-ttu-id="8f356-115">Não foi possível retornar o status do pai.</span><span class="sxs-lookup"><span data-stu-id="8f356-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="8f356-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8f356-116">E_INVALIDARG</span></span>|<span data-ttu-id="8f356-117">`pPotentialParentFrame` ou `pIsParent` é nulo.</span><span class="sxs-lookup"><span data-stu-id="8f356-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8f356-118">Exceções</span><span class="sxs-lookup"><span data-stu-id="8f356-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f356-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f356-119">Remarks</span></span>  
 <span data-ttu-id="8f356-120">`IsMatchingParentFrame`Retorna `true` se o objeto de quadro passar para o método é o pai do objeto de quadro no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="8f356-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="8f356-121">Se você chamar o método em um quadro que não é um filho do quadro especificado, ele retornará um erro.</span><span class="sxs-lookup"><span data-stu-id="8f356-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f356-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f356-122">Requirements</span></span>  
 <span data-ttu-id="8f356-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f356-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f356-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f356-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f356-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f356-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f356-126">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f356-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f356-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f356-127">See Also</span></span>  
 [<span data-ttu-id="8f356-128">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="8f356-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="8f356-129">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="8f356-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8f356-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="8f356-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: Método ICorDebugNativeFrame2::IsMatchingParentFrame
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: aa06b7db6b7371e66853ed242f5e118fb5e5ff0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096195"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="34349-102">Método ICorDebugNativeFrame2::IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="34349-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="34349-103">Determina se o quadro especificado é o pai do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="34349-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34349-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34349-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34349-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34349-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="34349-106">no Um ponteiro para o objeto de quadro que você deseja avaliar para o status pai.</span><span class="sxs-lookup"><span data-stu-id="34349-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="34349-107">[fora] `true` se `pPotentialParentFrame` for o pai do quadro atual; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="34349-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34349-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="34349-108">Return Value</span></span>  
 <span data-ttu-id="34349-109">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="34349-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="34349-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34349-110">HRESULT</span></span>|<span data-ttu-id="34349-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="34349-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34349-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="34349-112">S_OK</span></span>|<span data-ttu-id="34349-113">O status pai foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="34349-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="34349-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34349-114">E_FAIL</span></span>|<span data-ttu-id="34349-115">Não foi possível retornar o status pai.</span><span class="sxs-lookup"><span data-stu-id="34349-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="34349-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="34349-116">E_INVALIDARG</span></span>|<span data-ttu-id="34349-117">`pPotentialParentFrame` ou `pIsParent` é nulo.</span><span class="sxs-lookup"><span data-stu-id="34349-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="34349-118">Exceções</span><span class="sxs-lookup"><span data-stu-id="34349-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34349-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="34349-119">Remarks</span></span>  
 <span data-ttu-id="34349-120">`IsMatchingParentFrame` retornará `true` se o objeto de quadro passado para o método for o pai do objeto de quadro no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="34349-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="34349-121">Se você chamar o método em um quadro que não seja um filho do quadro especificado, ele retornará um erro.</span><span class="sxs-lookup"><span data-stu-id="34349-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34349-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34349-122">Requirements</span></span>  
 <span data-ttu-id="34349-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34349-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34349-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34349-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34349-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34349-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34349-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34349-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34349-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34349-127">See also</span></span>

- [<span data-ttu-id="34349-128">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="34349-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="34349-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="34349-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="34349-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="34349-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

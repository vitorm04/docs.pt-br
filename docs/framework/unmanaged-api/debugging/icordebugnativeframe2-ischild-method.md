---
title: Método ICorDebugNativeFrame2::IsChild
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550d25e995bdfe010fb1aa664a7c9882a775f4d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757164"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="c18d3-102">Método ICorDebugNativeFrame2::IsChild</span><span class="sxs-lookup"><span data-stu-id="c18d3-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="c18d3-103">Determina se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="c18d3-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c18d3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c18d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c18d3-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="c18d3-106">[out] Um valor booliano que especifica se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="c18d3-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c18d3-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c18d3-107">Return Value</span></span>  
 <span data-ttu-id="c18d3-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="c18d3-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c18d3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c18d3-109">HRESULT</span></span>|<span data-ttu-id="c18d3-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c18d3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c18d3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c18d3-111">S_OK</span></span>|<span data-ttu-id="c18d3-112">O status de filho foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c18d3-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="c18d3-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c18d3-113">E_FAIL</span></span>|<span data-ttu-id="c18d3-114">Não foi possível retornar o status de filho.</span><span class="sxs-lookup"><span data-stu-id="c18d3-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="c18d3-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c18d3-115">E_INVALIDARG</span></span>|<span data-ttu-id="c18d3-116">`pIsChild` é nulo.</span><span class="sxs-lookup"><span data-stu-id="c18d3-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="c18d3-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="c18d3-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c18d3-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="c18d3-118">Remarks</span></span>  
 <span data-ttu-id="c18d3-119">O `IsChild` método retorna `true` se o objeto de quadro no qual você chama o método é um filho de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="c18d3-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="c18d3-120">Se esse for o caso, use o [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) método para verificar se um quadro é seu pai.</span><span class="sxs-lookup"><span data-stu-id="c18d3-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c18d3-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c18d3-121">Requirements</span></span>  
 <span data-ttu-id="c18d3-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c18d3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c18d3-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c18d3-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c18d3-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c18d3-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c18d3-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c18d3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c18d3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c18d3-126">See also</span></span>

- [<span data-ttu-id="c18d3-127">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="c18d3-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="c18d3-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c18d3-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c18d3-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="c18d3-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

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
ms.openlocfilehash: 539fa612234c4cc37bed5a8fd4b1e727a35b1d6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096386"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="dbb85-102">Método ICorDebugNativeFrame2::IsChild</span><span class="sxs-lookup"><span data-stu-id="dbb85-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="dbb85-103">Determina se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="dbb85-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbb85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbb85-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbb85-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbb85-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="dbb85-106">fora Um valor booliano que especifica se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="dbb85-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbb85-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dbb85-107">Return Value</span></span>  
 <span data-ttu-id="dbb85-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="dbb85-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dbb85-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbb85-109">HRESULT</span></span>|<span data-ttu-id="dbb85-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbb85-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbb85-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbb85-111">S_OK</span></span>|<span data-ttu-id="dbb85-112">O status filho foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dbb85-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="dbb85-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbb85-113">E_FAIL</span></span>|<span data-ttu-id="dbb85-114">Não foi possível retornar o status filho.</span><span class="sxs-lookup"><span data-stu-id="dbb85-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="dbb85-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="dbb85-115">E_INVALIDARG</span></span>|<span data-ttu-id="dbb85-116">`pIsChild` é nulo.</span><span class="sxs-lookup"><span data-stu-id="dbb85-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="dbb85-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="dbb85-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbb85-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbb85-118">Remarks</span></span>  
 <span data-ttu-id="dbb85-119">O método `IsChild` retorna `true` se o objeto de quadro no qual você chama o método é filho de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="dbb85-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="dbb85-120">Se esse for o caso, use o método [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) para verificar se um quadro é seu pai.</span><span class="sxs-lookup"><span data-stu-id="dbb85-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbb85-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbb85-121">Requirements</span></span>  
 <span data-ttu-id="dbb85-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbb85-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbb85-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbb85-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbb85-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbb85-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbb85-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbb85-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb85-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbb85-126">See also</span></span>

- [<span data-ttu-id="dbb85-127">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="dbb85-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="dbb85-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="dbb85-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="dbb85-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="dbb85-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

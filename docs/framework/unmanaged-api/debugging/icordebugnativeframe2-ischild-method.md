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
ms.openlocfilehash: 22722e4d602bdb9df9877b2199b4d4271a4d3105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792727"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="ce7c6-102">Método ICorDebugNativeFrame2::IsChild</span><span class="sxs-lookup"><span data-stu-id="ce7c6-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="ce7c6-103">Determina se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="ce7c6-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce7c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce7c6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce7c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce7c6-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="ce7c6-106">fora Um valor booliano que especifica se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="ce7c6-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce7c6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ce7c6-107">Return Value</span></span>  
 <span data-ttu-id="ce7c6-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="ce7c6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ce7c6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce7c6-109">HRESULT</span></span>|<span data-ttu-id="ce7c6-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce7c6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce7c6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce7c6-111">S_OK</span></span>|<span data-ttu-id="ce7c6-112">O status filho foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ce7c6-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="ce7c6-113">{1&gt;E_FAIL&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ce7c6-113">E_FAIL</span></span>|<span data-ttu-id="ce7c6-114">Não foi possível retornar o status filho.</span><span class="sxs-lookup"><span data-stu-id="ce7c6-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="ce7c6-115">{1&gt;E_INVALIDARG&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ce7c6-115">E_INVALIDARG</span></span>|<span data-ttu-id="ce7c6-116">`pIsChild` é nulo.</span><span class="sxs-lookup"><span data-stu-id="ce7c6-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ce7c6-117">Exceções</span><span class="sxs-lookup"><span data-stu-id="ce7c6-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce7c6-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce7c6-118">Remarks</span></span>  
 <span data-ttu-id="ce7c6-119">O método `IsChild` retorna `true` se o objeto de quadro no qual você chama o método é filho de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="ce7c6-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="ce7c6-120">Se esse for o caso, use o método [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) para verificar se um quadro é seu pai.</span><span class="sxs-lookup"><span data-stu-id="ce7c6-120">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce7c6-121">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ce7c6-121">Requirements</span></span>  
 <span data-ttu-id="ce7c6-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce7c6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce7c6-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce7c6-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce7c6-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce7c6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce7c6-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce7c6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7c6-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="ce7c6-126">See also</span></span>

- [<span data-ttu-id="ce7c6-127">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="ce7c6-127">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="ce7c6-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ce7c6-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ce7c6-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="ce7c6-129">Debugging</span></span>](index.md)

---
title: Método ICorDebugInternalFrame2::GetFrameAddress
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: 40e64bdb35cff4e6ad6132c0806cfddd2767443c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122683"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="a77aa-102">Método ICorDebugInternalFrame2::GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="a77aa-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="a77aa-103">Retorna o endereço da pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="a77aa-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a77aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a77aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a77aa-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="a77aa-106">fora Ponteiro para a `CORDB_ADDRESS` do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="a77aa-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a77aa-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a77aa-107">Return Value</span></span>  
 <span data-ttu-id="a77aa-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="a77aa-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a77aa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a77aa-109">HRESULT</span></span>|<span data-ttu-id="a77aa-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a77aa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a77aa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a77aa-111">S_OK</span></span>|<span data-ttu-id="a77aa-112">O endereço do quadro interno foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a77aa-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="a77aa-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a77aa-113">E_FAIL</span></span>|<span data-ttu-id="a77aa-114">Não foi possível retornar o endereço do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="a77aa-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="a77aa-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a77aa-115">E_INVALIDARG</span></span>|<span data-ttu-id="a77aa-116">`pAddress` é `null`.</span><span class="sxs-lookup"><span data-stu-id="a77aa-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a77aa-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="a77aa-117">Remarks</span></span>  
 <span data-ttu-id="a77aa-118">O valor retornado em `pAddress` pode ser usado para determinar o local do quadro interno em relação a outros quadros na pilha.</span><span class="sxs-lookup"><span data-stu-id="a77aa-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="a77aa-119">Mesmo em computadores baseados em IA-64, o quadro interno reside somente na pilha e não há nenhum ponteiro correspondente para um repositório de backup.</span><span class="sxs-lookup"><span data-stu-id="a77aa-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a77aa-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a77aa-120">Requirements</span></span>  
 <span data-ttu-id="a77aa-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a77aa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a77aa-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a77aa-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a77aa-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a77aa-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a77aa-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a77aa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a77aa-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a77aa-125">See also</span></span>

- [<span data-ttu-id="a77aa-126">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="a77aa-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="a77aa-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a77aa-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a77aa-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="a77aa-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

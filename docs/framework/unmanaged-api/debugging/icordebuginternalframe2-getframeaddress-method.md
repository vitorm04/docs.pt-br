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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c30115a23f7f73662c9b3f4f4a09d45478ad687
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187285"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="9304d-102">Método ICorDebugInternalFrame2::GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="9304d-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="9304d-103">Retorna o endereço de pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="9304d-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9304d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9304d-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9304d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9304d-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="9304d-106">[out] Ponteiro para o `CORDB_ADDRESS` para o quadro interno.</span><span class="sxs-lookup"><span data-stu-id="9304d-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9304d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9304d-107">Return Value</span></span>  
 <span data-ttu-id="9304d-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="9304d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9304d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9304d-109">HRESULT</span></span>|<span data-ttu-id="9304d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9304d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9304d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9304d-111">S_OK</span></span>|<span data-ttu-id="9304d-112">O endereço do quadro interno foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9304d-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="9304d-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9304d-113">E_FAIL</span></span>|<span data-ttu-id="9304d-114">Não foi possível retornar o endereço do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="9304d-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="9304d-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9304d-115">E_INVALIDARG</span></span>|`pAddress` <span data-ttu-id="9304d-116">is `null`.</span><span class="sxs-lookup"><span data-stu-id="9304d-116">is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9304d-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="9304d-117">Remarks</span></span>  
 <span data-ttu-id="9304d-118">O valor retornado na `pAddress` pode ser usado para determinar o local do quadro interno em relação a outros quadros na pilha.</span><span class="sxs-lookup"><span data-stu-id="9304d-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="9304d-119">Mesmo em computadores baseados em IA-64, o quadro interno reside na pilha apenas e não há nenhum ponteiro correspondente para um armazenamento de backup.</span><span class="sxs-lookup"><span data-stu-id="9304d-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9304d-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9304d-120">Requirements</span></span>  
 <span data-ttu-id="9304d-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9304d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9304d-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9304d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9304d-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9304d-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9304d-124">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9304d-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9304d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9304d-125">See also</span></span>

- [<span data-ttu-id="9304d-126">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="9304d-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="9304d-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9304d-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9304d-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="9304d-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

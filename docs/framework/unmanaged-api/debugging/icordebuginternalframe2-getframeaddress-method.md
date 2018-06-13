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
ms.openlocfilehash: d088aaaaa80ee3513a37ea0345d720832504c005
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421142"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="82f55-102">Método ICorDebugInternalFrame2::GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="82f55-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="82f55-103">Retorna o endereço de pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="82f55-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f55-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82f55-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82f55-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82f55-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="82f55-106">[out] Ponteiro para o `CORDB_ADDRESS` para o quadro interno.</span><span class="sxs-lookup"><span data-stu-id="82f55-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82f55-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="82f55-107">Return Value</span></span>  
 <span data-ttu-id="82f55-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="82f55-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="82f55-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82f55-109">HRESULT</span></span>|<span data-ttu-id="82f55-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="82f55-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82f55-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="82f55-111">S_OK</span></span>|<span data-ttu-id="82f55-112">O endereço do quadro interno foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="82f55-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="82f55-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82f55-113">E_FAIL</span></span>|<span data-ttu-id="82f55-114">Não foi possível retornar o endereço do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="82f55-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="82f55-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="82f55-115">E_INVALIDARG</span></span>|<span data-ttu-id="82f55-116">`pAddress` é `null`.</span><span class="sxs-lookup"><span data-stu-id="82f55-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82f55-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="82f55-117">Remarks</span></span>  
 <span data-ttu-id="82f55-118">O valor retornado em `pAddress` pode ser usado para determinar o local do quadro interno em relação a outros quadros na pilha.</span><span class="sxs-lookup"><span data-stu-id="82f55-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="82f55-119">Mesmo em computadores baseados em IA-64, o quadro interno reside na pilha apenas e não há nenhum ponteiro correspondente a um armazenamento de backup.</span><span class="sxs-lookup"><span data-stu-id="82f55-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f55-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82f55-120">Requirements</span></span>  
 <span data-ttu-id="82f55-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82f55-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f55-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82f55-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82f55-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82f55-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82f55-124">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f55-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f55-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82f55-125">See Also</span></span>  
 [<span data-ttu-id="82f55-126">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="82f55-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="82f55-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="82f55-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="82f55-128">Depuração</span><span class="sxs-lookup"><span data-stu-id="82f55-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

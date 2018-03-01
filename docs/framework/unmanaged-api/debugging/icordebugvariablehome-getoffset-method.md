---
title: "Método ICorDebugVariableHome::GetOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09f80a362d4b44d13c39218b9d7a0db11ef49f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="7da5e-102">Método ICorDebugVariableHome::GetOffset</span><span class="sxs-lookup"><span data-stu-id="7da5e-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="7da5e-103">Obtém o deslocamento do registro base para uma variável.</span><span class="sxs-lookup"><span data-stu-id="7da5e-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da5e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7da5e-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7da5e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7da5e-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="7da5e-106">[out] O deslocamento do registro base.</span><span class="sxs-lookup"><span data-stu-id="7da5e-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7da5e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7da5e-107">Return Value</span></span>  
 <span data-ttu-id="7da5e-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7da5e-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="7da5e-109">Valor</span><span class="sxs-lookup"><span data-stu-id="7da5e-109">Value</span></span>|<span data-ttu-id="7da5e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7da5e-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="7da5e-111">A variável está em um local relativo ao registro de memória.</span><span class="sxs-lookup"><span data-stu-id="7da5e-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="7da5e-112">A variável não está em um local relativo ao registro de memória.</span><span class="sxs-lookup"><span data-stu-id="7da5e-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7da5e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7da5e-113">Requirements</span></span>  
 <span data-ttu-id="7da5e-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7da5e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7da5e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7da5e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7da5e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7da5e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7da5e-117">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7da5e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da5e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7da5e-118">See Also</span></span>  
 [<span data-ttu-id="7da5e-119">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="7da5e-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

---
title: "Método ICorDebugChain::GetRegisterSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2463c0860591a9642ac52a333b7540549d7e9183
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="ff72d-102">Método ICorDebugChain::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="ff72d-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="ff72d-103">Obtém o conjunto de registros de parte ativa dessa cadeia.</span><span class="sxs-lookup"><span data-stu-id="ff72d-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff72d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff72d-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff72d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff72d-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="ff72d-106">[out] Um ponteiro para o endereço de um [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) conjunto de objetos que representa o registro para a parte ativa dessa cadeia.</span><span class="sxs-lookup"><span data-stu-id="ff72d-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff72d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff72d-107">Requirements</span></span>  
 <span data-ttu-id="ff72d-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff72d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff72d-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff72d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff72d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff72d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff72d-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff72d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

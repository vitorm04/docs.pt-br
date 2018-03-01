---
title: "Método ICorDebugNativeFrame::GetRegisterSet"
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
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28fb7b2fde484e2608a4d84215755df9a77a73b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="30fa4-102">Método ICorDebugNativeFrame::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="30fa4-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="30fa4-103">Obtém o conjunto de registros deste quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="30fa4-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30fa4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30fa4-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30fa4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30fa4-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="30fa4-106">[out] Um ponteiro para o endereço de um [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) conjunto de objetos que representa o registro para este quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="30fa4-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30fa4-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30fa4-107">Requirements</span></span>  
 <span data-ttu-id="30fa4-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30fa4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30fa4-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30fa4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30fa4-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30fa4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30fa4-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30fa4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30fa4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30fa4-112">See Also</span></span>  
 

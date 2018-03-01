---
title: "Método ICorDebugController::Detach"
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
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59fe2c4bfbd91afd263a0ada1eb355aaa8914aa2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="e4756-102">Método ICorDebugController::Detach</span><span class="sxs-lookup"><span data-stu-id="e4756-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="e4756-103">Desanexa o depurador do domínio de aplicativo ou processo.</span><span class="sxs-lookup"><span data-stu-id="e4756-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4756-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4756-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e4756-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4756-105">Remarks</span></span>  
 <span data-ttu-id="e4756-106">O domínio de aplicativo ou processo continua a execução normalmente, mas o objeto "ICorDebugProcess" ou "ICorDebugAppDomain" não é mais válido e nenhum retorno de chamada mais ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="e4756-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="e4756-107">O .NET Framework versão 2.0, se a depuração não gerenciada está habilitado, esse método irá falhar devido a limitações de sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e4756-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4756-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4756-108">Requirements</span></span>  
 <span data-ttu-id="e4756-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4756-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4756-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4756-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4756-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4756-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4756-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4756-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4756-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4756-113">See Also</span></span>  
 

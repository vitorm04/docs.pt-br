---
title: Método ICorDebugController::Detach
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a9bde77f7c393756ec1d3e7d30b96392aa6a94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151795"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="95c00-102">Método ICorDebugController::Detach</span><span class="sxs-lookup"><span data-stu-id="95c00-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="95c00-103">Desanexa o depurador do domínio de aplicativo ou processo.</span><span class="sxs-lookup"><span data-stu-id="95c00-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c00-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95c00-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="95c00-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="95c00-105">Remarks</span></span>  
 <span data-ttu-id="95c00-106">O domínio de aplicativo ou processo continua normalmente, a execução, mas o objeto "ICorDebugProcess" ou "ICorDebugAppDomain" não é mais válido e mais nenhum retorno de chamada será feita.</span><span class="sxs-lookup"><span data-stu-id="95c00-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="95c00-107">No .NET Framework versão 2.0, se a depuração não gerenciada está habilitada, esse método irá falhar devido a limitações de sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="95c00-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c00-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95c00-108">Requirements</span></span>  
 <span data-ttu-id="95c00-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c00-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c00-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95c00-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95c00-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95c00-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="95c00-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="95c00-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95c00-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95c00-113">See also</span></span>

---
title: "Método ICorDebugAppDomain::EnumerateSteppers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.EnumerateSteppers
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b410eabee546307488449e577d9e102ac6a210b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="299f3-102">Método ICorDebugAppDomain::EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="299f3-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="299f3-103">Obtém um enumerador para todos os steppers ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="299f3-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="299f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="299f3-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="299f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="299f3-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="299f3-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugStepperEnum que é o enumerador para todos os steppers ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="299f3-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="299f3-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="299f3-107">Requirements</span></span>  
 <span data-ttu-id="299f3-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="299f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="299f3-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="299f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="299f3-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="299f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="299f3-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="299f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

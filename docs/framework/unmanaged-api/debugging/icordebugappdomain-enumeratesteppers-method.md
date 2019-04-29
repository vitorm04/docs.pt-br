---
title: Método ICorDebugAppDomain::EnumerateSteppers
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d326c801ed17fa6fe79f9e464e64844d0016e572
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785145"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="912d3-102">Método ICorDebugAppDomain::EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="912d3-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="912d3-103">Obtém um enumerador para todos os steppers Active Directory no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="912d3-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="912d3-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="912d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="912d3-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="912d3-106">[out] Um ponteiro para o endereço de um objeto ICorDebugStepperEnum que é o enumerador para todos os steppers Active Directory no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="912d3-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="912d3-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="912d3-107">Requirements</span></span>  
 <span data-ttu-id="912d3-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="912d3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="912d3-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="912d3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="912d3-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="912d3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="912d3-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912d3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

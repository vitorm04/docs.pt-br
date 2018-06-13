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
ms.openlocfilehash: 7bf3aa6d883dffece6ba89d41005499cc6206906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401285"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="38977-102">Método ICorDebugAppDomain::EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="38977-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="38977-103">Obtém um enumerador para todos os steppers ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38977-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38977-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38977-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38977-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38977-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="38977-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugStepperEnum que é o enumerador para todos os steppers ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38977-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38977-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38977-107">Requirements</span></span>  
 <span data-ttu-id="38977-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38977-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38977-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38977-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38977-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38977-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38977-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38977-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

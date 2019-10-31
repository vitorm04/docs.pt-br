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
ms.openlocfilehash: a736990188023031eb8df5a76dd16fcc289cfe20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134030"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="5230a-102">Método ICorDebugAppDomain::EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="5230a-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="5230a-103">Obtém um enumerador para todos os percorridos ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5230a-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5230a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5230a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5230a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5230a-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="5230a-106">fora Um ponteiro para o endereço de um objeto ICorDebugStepperEnum que é o enumerador para todos os perparadores ativos no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5230a-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5230a-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5230a-107">Requirements</span></span>  
 <span data-ttu-id="5230a-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5230a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5230a-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5230a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5230a-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5230a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5230a-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5230a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

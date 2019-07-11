---
title: Método ICorDebugStepper2::SetJMC
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c6b53d23410dd310766dab44664c8cd865ee9ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771687"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="5779f-102">Método ICorDebugStepper2::SetJMC</span><span class="sxs-lookup"><span data-stu-id="5779f-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="5779f-103">Define um valor que especifica se este ICorDebugStepper etapas somente por meio de código que é criado pelo desenvolvedor do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5779f-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="5779f-104">Esse processo também é conhecido apenas como meu depuração de código (JMC).</span><span class="sxs-lookup"><span data-stu-id="5779f-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5779f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5779f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5779f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5779f-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="5779f-107">[in] Definido como `true` para a etapa apenas por meio de código que é criado pelo desenvolvedor do aplicativo; caso contrário, definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="5779f-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5779f-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5779f-108">Requirements</span></span>  
 <span data-ttu-id="5779f-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5779f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5779f-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5779f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5779f-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5779f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5779f-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5779f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

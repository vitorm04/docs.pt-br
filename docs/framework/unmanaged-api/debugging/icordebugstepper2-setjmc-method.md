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
ms.openlocfilehash: ab1351af042aba5042cc7a04614bc3cf14f7d7ae
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379469"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="4eeb4-102">Método ICorDebugStepper2::SetJMC</span><span class="sxs-lookup"><span data-stu-id="4eeb4-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="4eeb4-103">Define um valor que especifica se este ICorDebugStepper etapas somente por meio de código que é criado pelo desenvolvedor de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4eeb4-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="4eeb4-104">Esse processo também é conhecido como depuração de apenas meu código (JMC).</span><span class="sxs-lookup"><span data-stu-id="4eeb4-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eeb4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4eeb4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4eeb4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4eeb4-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="4eeb4-107">no Defina como `true` Step somente por meio de código que é criado pelo desenvolvedor de um aplicativo; caso contrário, defina como `false` .</span><span class="sxs-lookup"><span data-stu-id="4eeb4-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eeb4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4eeb4-108">Requirements</span></span>  
 <span data-ttu-id="4eeb4-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eeb4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eeb4-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4eeb4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4eeb4-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4eeb4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4eeb4-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eeb4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

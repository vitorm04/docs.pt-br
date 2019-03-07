---
title: Método ICorDebugStepper::SetUnmappedStopMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da799b0d4f4e5e4b281445baa35d95f992ba0b63
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474950"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="79f74-102">Método ICorDebugStepper::SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="79f74-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="79f74-103">Define um valor que especifica o tipo de código não mapeado no qual a execução será interrompida.</span><span class="sxs-lookup"><span data-stu-id="79f74-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79f74-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79f74-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79f74-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="79f74-106">[in] Um valor de enumeração CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual o depurador interromperá a execução.</span><span class="sxs-lookup"><span data-stu-id="79f74-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="79f74-107">O valor padrão é STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="79f74-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="79f74-108">O valor STOP_UNMANAGED só é válido com a depuração de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="79f74-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79f74-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="79f74-109">Remarks</span></span>  
 <span data-ttu-id="79f74-110">Quando o depurador encontra uma just-in-time (compilação JIT) que não tem nenhum mapeamento correspondente para Microsoft intermediate language (MSIL), ele interromperá a execução se o sinalizador que especifica esse tipo de código não mapeado tiver sido definido; Caso contrário, depuração de modo transparente continua.</span><span class="sxs-lookup"><span data-stu-id="79f74-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="79f74-111">Se o depurador não usa um seletor para inserir um método, em seguida, ele não necessariamente passar por código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="79f74-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79f74-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79f74-112">Requirements</span></span>  
 <span data-ttu-id="79f74-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79f74-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79f74-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79f74-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79f74-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79f74-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79f74-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79f74-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

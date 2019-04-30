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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987448"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="507eb-102">Método ICorDebugStepper::SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="507eb-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="507eb-103">Define um valor que especifica o tipo de código não mapeado no qual a execução será interrompida.</span><span class="sxs-lookup"><span data-stu-id="507eb-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="507eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="507eb-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="507eb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="507eb-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="507eb-106">[in] Um valor de enumeração CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual o depurador interromperá a execução.</span><span class="sxs-lookup"><span data-stu-id="507eb-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="507eb-107">O valor padrão é STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="507eb-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="507eb-108">O valor STOP_UNMANAGED só é válido com a depuração de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="507eb-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="507eb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="507eb-109">Remarks</span></span>  
 <span data-ttu-id="507eb-110">Quando o depurador encontra uma just-in-time (compilação JIT) que não tem nenhum mapeamento correspondente para Microsoft intermediate language (MSIL), ele interromperá a execução se o sinalizador que especifica esse tipo de código não mapeado tiver sido definido; Caso contrário, depuração de modo transparente continua.</span><span class="sxs-lookup"><span data-stu-id="507eb-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="507eb-111">Se o depurador não usa um seletor para inserir um método, em seguida, ele não necessariamente passar por código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="507eb-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="507eb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="507eb-112">Requirements</span></span>  
 <span data-ttu-id="507eb-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="507eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="507eb-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="507eb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="507eb-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="507eb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="507eb-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="507eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

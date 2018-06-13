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
ms.openlocfilehash: dc4e51ec60c7526f36bbe4909bec91a527e0862c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419904"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="864fb-102">Método ICorDebugStepper::SetUnmappedStopMask</span><span class="sxs-lookup"><span data-stu-id="864fb-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="864fb-103">Define um valor que especifica o tipo de código não mapeado no qual a execução será interrompida.</span><span class="sxs-lookup"><span data-stu-id="864fb-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="864fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="864fb-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="864fb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="864fb-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="864fb-106">[in] Um valor da enumeração CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual o depurador interromperá a execução.</span><span class="sxs-lookup"><span data-stu-id="864fb-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="864fb-107">O valor padrão é STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="864fb-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="864fb-108">O valor STOP_UNMANAGED só é válido com depuração interop.</span><span class="sxs-lookup"><span data-stu-id="864fb-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="864fb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="864fb-109">Remarks</span></span>  
 <span data-ttu-id="864fb-110">Quando o depurador encontra a compilação um just-in-time (JIT) que não tem nenhum mapeamento correspondente para Microsoft intermediate language (MSIL), ele interrompe a execução se o sinalizador que especifica que tipo de código não mapeado tiver sido definido; Caso contrário, passo a passo transparentemente continua.</span><span class="sxs-lookup"><span data-stu-id="864fb-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="864fb-111">Se o depurador não usa um seletor para inserir um método, em seguida, ele não necessariamente passar por código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="864fb-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="864fb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="864fb-112">Requirements</span></span>  
 <span data-ttu-id="864fb-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="864fb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="864fb-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="864fb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="864fb-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="864fb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="864fb-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="864fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

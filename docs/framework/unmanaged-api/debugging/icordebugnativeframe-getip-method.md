---
title: "Método ICorDebugNativeFrame::GetIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f9ea20577b3132a2378013e7c5fa8356c14c8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="d3a55-102">Método ICorDebugNativeFrame::GetIP</span><span class="sxs-lookup"><span data-stu-id="d3a55-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="d3a55-103">Obtém o código nativo deslocamento local para o qual o ponteiro de instrução é definido no momento.</span><span class="sxs-lookup"><span data-stu-id="d3a55-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a55-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3a55-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3a55-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d3a55-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="d3a55-106">[out] Um ponteiro para o local de deslocamento no código nativo.</span><span class="sxs-lookup"><span data-stu-id="d3a55-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3a55-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3a55-107">Remarks</span></span>  
 <span data-ttu-id="d3a55-108">Se o quadro de pilha é representado por esse "ICorDebugNativeFrame" estiver ativo, o deslocamento é o endereço da próxima instrução a ser executada.</span><span class="sxs-lookup"><span data-stu-id="d3a55-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="d3a55-109">Se este quadro de pilha não estiver ativo, o deslocamento é o endereço da próxima instrução a ser executado quando o quadro de pilhas é reativado.</span><span class="sxs-lookup"><span data-stu-id="d3a55-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3a55-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3a55-110">Requirements</span></span>  
 <span data-ttu-id="d3a55-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3a55-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3a55-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3a55-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3a55-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3a55-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3a55-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3a55-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a55-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3a55-115">See Also</span></span>  
 

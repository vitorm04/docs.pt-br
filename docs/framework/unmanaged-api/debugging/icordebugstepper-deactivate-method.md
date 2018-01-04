---
title: "Método ICorDebugStepper::Deactivate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Deactivate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1541c6fa838115655c3ff176a0cb29f803733daa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="4a2d5-102">Método ICorDebugStepper::Deactivate</span><span class="sxs-lookup"><span data-stu-id="4a2d5-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="4a2d5-103">Faz com que este ICorDebugStepper cancelar o último comando da etapa que ele recebeu.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a2d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a2d5-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4a2d5-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a2d5-105">Remarks</span></span>  
 <span data-ttu-id="4a2d5-106">Um novo comando de depuração pode ser emitido após o comando de etapa recebido recentemente foi cancelado.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a2d5-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a2d5-107">Requirements</span></span>  
 <span data-ttu-id="4a2d5-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a2d5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a2d5-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a2d5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a2d5-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a2d5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a2d5-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a2d5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

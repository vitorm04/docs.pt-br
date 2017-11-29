---
title: "Método ICorDebugExceptionDebugEvent::GetFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33534a65f7a58981abd3df324b5fe005a06669d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="4a95e-102">Método ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="4a95e-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="4a95e-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="4a95e-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a95e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a95e-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a95e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a95e-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="4a95e-106">[out] Um ponteiro para um [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) valor que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="4a95e-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a95e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a95e-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a95e-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4a95e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a95e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a95e-109">Requirements</span></span>  
 <span data-ttu-id="4a95e-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a95e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a95e-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a95e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a95e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a95e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a95e-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a95e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a95e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a95e-114">See Also</span></span>  
 [<span data-ttu-id="4a95e-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="4a95e-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="4a95e-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="4a95e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.workload: dotnet
ms.openlocfilehash: c6e7767ca5467f69dc7f53728bda9daf5f08331c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="41c70-102">Método ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="41c70-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="41c70-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="41c70-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c70-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41c70-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41c70-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41c70-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="41c70-106">[out] Um ponteiro para um [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) valor que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="41c70-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41c70-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="41c70-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41c70-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="41c70-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c70-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41c70-109">Requirements</span></span>  
 <span data-ttu-id="41c70-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c70-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c70-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41c70-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41c70-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41c70-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41c70-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c70-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c70-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41c70-114">See Also</span></span>  
 [<span data-ttu-id="41c70-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="41c70-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="41c70-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="41c70-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

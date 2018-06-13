---
title: Método ICorDebugExceptionDebugEvent::GetFlags
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b9c07b010447b4a437febb4b60565111a85c8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415448"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="d6fe0-102">Método ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="d6fe0-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="d6fe0-103">Obtém um sinalizador que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="d6fe0-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6fe0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6fe0-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6fe0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6fe0-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="d6fe0-106">[out] Um ponteiro para um [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) valor que indica se a exceção pode ser interceptada.</span><span class="sxs-lookup"><span data-stu-id="d6fe0-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6fe0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6fe0-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6fe0-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d6fe0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6fe0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6fe0-109">Requirements</span></span>  
 <span data-ttu-id="d6fe0-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6fe0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6fe0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6fe0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6fe0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6fe0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6fe0-113">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6fe0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6fe0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6fe0-114">See Also</span></span>  
 [<span data-ttu-id="d6fe0-115">Interface ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="d6fe0-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="d6fe0-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d6fe0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

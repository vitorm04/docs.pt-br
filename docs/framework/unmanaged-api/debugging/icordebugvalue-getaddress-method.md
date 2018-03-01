---
title: "Método ICorDebugValue::GetAddress"
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
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8aa5a0c3740b6cf97d2a5d855343a36b90fd538
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="909d3-102">Método ICorDebugValue::GetAddress</span><span class="sxs-lookup"><span data-stu-id="909d3-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="909d3-103">Obtém o endereço do objeto "ICorDebugValue", que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="909d3-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="909d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="909d3-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="909d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="909d3-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="909d3-106">[out] Ponteiro para uma `CORDB_ADDRESS` objeto que especifica o endereço do objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="909d3-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="909d3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="909d3-107">Remarks</span></span>  
 <span data-ttu-id="909d3-108">Se o valor estiver disponível, será retornado 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="909d3-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="909d3-109">Isso pode acontecer se o valor for pelo menos parcialmente nos registros ou armazenados em um identificador de coletor de lixo (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="909d3-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="909d3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="909d3-110">Requirements</span></span>  
 <span data-ttu-id="909d3-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="909d3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="909d3-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="909d3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="909d3-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="909d3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="909d3-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="909d3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="909d3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="909d3-115">See Also</span></span>  
 

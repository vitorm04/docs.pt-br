---
title: "Método IDebuggerInfo::IsDebuggerAttached"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerInfo.IsDebuggerAttached
api_location: mscoree.dll
api_type: COM
f1_keywords: IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c241af6b71591374d8ce8cc8d1610a8dce91b2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="64066-102">Método IDebuggerInfo::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="64066-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="64066-103">Obtém um valor que indica se um depurador gerenciado está anexado a este processo.</span><span class="sxs-lookup"><span data-stu-id="64066-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64066-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64066-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64066-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64066-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="64066-106">[out] Um ponteiro para um valor que é `true` se um depurador gerenciado é anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="64066-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64066-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64066-107">Requirements</span></span>  
 <span data-ttu-id="64066-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64066-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64066-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="64066-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64066-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="64066-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64066-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64066-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64066-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64066-112">See Also</span></span>  
 [<span data-ttu-id="64066-113">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="64066-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)

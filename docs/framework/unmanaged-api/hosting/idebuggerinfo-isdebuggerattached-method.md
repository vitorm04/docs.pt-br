---
title: Método IDebuggerInfo::IsDebuggerAttached
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae7bc60abaedef8c3491a90eae01ebc02cff1ce
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469047"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="95aa6-102">Método IDebuggerInfo::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="95aa6-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="95aa6-103">Obtém um valor que indica se um depurador gerenciado está anexado a esse processo.</span><span class="sxs-lookup"><span data-stu-id="95aa6-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95aa6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95aa6-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95aa6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95aa6-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="95aa6-106">[out] Um ponteiro para um valor que é `true` se um depurador gerenciado é anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="95aa6-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95aa6-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95aa6-107">Requirements</span></span>  
 <span data-ttu-id="95aa6-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95aa6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95aa6-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95aa6-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95aa6-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="95aa6-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95aa6-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95aa6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95aa6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95aa6-112">See also</span></span>
- [<span data-ttu-id="95aa6-113">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="95aa6-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)

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
ms.openlocfilehash: 91acfa5545f3115c9e95207f05708ff32530994f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437275"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="05bd0-102">Método IDebuggerInfo::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="05bd0-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="05bd0-103">Obtém um valor que indica se um depurador gerenciado está anexado a este processo.</span><span class="sxs-lookup"><span data-stu-id="05bd0-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05bd0-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05bd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05bd0-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="05bd0-106">[out] Um ponteiro para um valor que é `true` se um depurador gerenciado é anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="05bd0-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05bd0-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05bd0-107">Requirements</span></span>  
 <span data-ttu-id="05bd0-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05bd0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05bd0-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05bd0-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05bd0-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="05bd0-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05bd0-111">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05bd0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bd0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05bd0-112">See Also</span></span>  
 [<span data-ttu-id="05bd0-113">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="05bd0-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)

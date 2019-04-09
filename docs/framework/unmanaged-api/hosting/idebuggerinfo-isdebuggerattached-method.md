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
ms.openlocfilehash: 0708a3b501a99b5f71be5ba4c6cc4ea2b754d12a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191335"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="6b7f0-102">Método IDebuggerInfo::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="6b7f0-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="6b7f0-103">Obtém um valor que indica se um depurador gerenciado está anexado a esse processo.</span><span class="sxs-lookup"><span data-stu-id="6b7f0-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b7f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b7f0-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b7f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b7f0-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="6b7f0-106">[out] Um ponteiro para um valor que é `true` se um depurador gerenciado é anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6b7f0-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b7f0-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b7f0-107">Requirements</span></span>  
 <span data-ttu-id="6b7f0-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b7f0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b7f0-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b7f0-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b7f0-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6b7f0-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6b7f0-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6b7f0-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b7f0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b7f0-112">See also</span></span>

- [<span data-ttu-id="6b7f0-113">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="6b7f0-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)

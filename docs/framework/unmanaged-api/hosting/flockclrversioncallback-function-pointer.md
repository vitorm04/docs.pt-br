---
title: "Ponteiro de função FLockClrVersionCallback"
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
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90b3bd053eb2e1161d6bb107afe9b3c627b1b207
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="feb00-102">Ponteiro de função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="feb00-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="feb00-103">Aponta para uma função que as chamadas de runtime (CLR) de linguagem comum para indicar que a inicialização foi iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="feb00-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="feb00-104">Este ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feb00-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb00-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="feb00-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="feb00-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="feb00-106">Remarks</span></span>  
 <span data-ttu-id="feb00-107">Essa função é implementada pelo host.</span><span class="sxs-lookup"><span data-stu-id="feb00-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb00-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="feb00-108">Requirements</span></span>  
 <span data-ttu-id="feb00-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feb00-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feb00-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="feb00-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="feb00-111">**Biblioteca:** arquivo MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="feb00-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="feb00-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feb00-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb00-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feb00-113">See Also</span></span>  
 [<span data-ttu-id="feb00-114">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="feb00-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 [<span data-ttu-id="feb00-115">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="feb00-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

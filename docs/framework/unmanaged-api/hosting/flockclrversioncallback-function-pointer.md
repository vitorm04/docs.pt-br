---
title: "Ponteiro de função FLockClrVersionCallback"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FLockClrVersionCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: FLockClrVersionCallback
helpviewer_keywords: FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca1b97c509ea8ed2c43c30cab278048aeb4170a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="7542a-102">Ponteiro de função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="7542a-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="7542a-103">Aponta para uma função que as chamadas de runtime (CLR) de linguagem comum para indicar que a inicialização foi iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="7542a-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="7542a-104">Este ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7542a-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7542a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7542a-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="7542a-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="7542a-106">Remarks</span></span>  
 <span data-ttu-id="7542a-107">Essa função é implementada pelo host.</span><span class="sxs-lookup"><span data-stu-id="7542a-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7542a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7542a-108">Requirements</span></span>  
 <span data-ttu-id="7542a-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7542a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7542a-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7542a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7542a-111">**Biblioteca:** arquivo MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="7542a-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="7542a-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7542a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7542a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7542a-113">See Also</span></span>  
 [<span data-ttu-id="7542a-114">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="7542a-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 [<span data-ttu-id="7542a-115">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="7542a-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

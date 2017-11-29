---
title: Interface ICLRPolicyManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager
helpviewer_keywords: ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3dd904184b730a5b0f5b2dfcac4197e708544d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="df03e-102">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="df03e-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="df03e-103">Fornece métodos que permitem que o host especificar ações de política a ser executada no caso de falhas e tempos limite.</span><span class="sxs-lookup"><span data-stu-id="df03e-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df03e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="df03e-104">Methods</span></span>  
  
|<span data-ttu-id="df03e-105">Método</span><span class="sxs-lookup"><span data-stu-id="df03e-105">Method</span></span>|<span data-ttu-id="df03e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="df03e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df03e-107">Método SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="df03e-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="df03e-108">Especifica a ação de política, que o common language runtime (CLR) deve ser executada quando ocorre a falha especificada.</span><span class="sxs-lookup"><span data-stu-id="df03e-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="df03e-109">Método SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="df03e-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="df03e-110">Especifica a ação de política que CLR deve ser executada quando a operação especificada expire.</span><span class="sxs-lookup"><span data-stu-id="df03e-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="df03e-111">Método SetDefaultAction</span><span class="sxs-lookup"><span data-stu-id="df03e-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="df03e-112">Especifica a ação de política que CLR deve ser executada quando ocorre a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="df03e-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="df03e-113">Método SetTimeout</span><span class="sxs-lookup"><span data-stu-id="df03e-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="df03e-114">Define um valor de tempo limite para a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="df03e-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="df03e-115">Método SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="df03e-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="df03e-116">Define um valor de tempo limite para a operação especificada e especifica a ação de política que CLR deve ser executada quando ocorre a operação.</span><span class="sxs-lookup"><span data-stu-id="df03e-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="df03e-117">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="df03e-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="df03e-118">Especifica o comportamento do CLR quando ocorre uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="df03e-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df03e-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df03e-119">Requirements</span></span>  
 <span data-ttu-id="df03e-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df03e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df03e-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df03e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df03e-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="df03e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df03e-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df03e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df03e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df03e-124">See Also</span></span>  
 [<span data-ttu-id="df03e-125">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="df03e-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="df03e-126">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="df03e-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="df03e-127">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="df03e-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="df03e-128">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="df03e-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)

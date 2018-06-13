---
title: Interface ICLRPolicyManager
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e8a1b1bcf4470f5e754775b1137b8221ae1d0b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435141"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="6e30f-102">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="6e30f-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="6e30f-103">Fornece métodos que permitem que o host especificar ações de política a ser executada no caso de falhas e tempos limite.</span><span class="sxs-lookup"><span data-stu-id="6e30f-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e30f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6e30f-104">Methods</span></span>  
  
|<span data-ttu-id="6e30f-105">Método</span><span class="sxs-lookup"><span data-stu-id="6e30f-105">Method</span></span>|<span data-ttu-id="6e30f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e30f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e30f-107">Método SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="6e30f-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="6e30f-108">Especifica a ação de política, que o common language runtime (CLR) deve ser executada quando ocorre a falha especificada.</span><span class="sxs-lookup"><span data-stu-id="6e30f-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="6e30f-109">Método SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="6e30f-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="6e30f-110">Especifica a ação de política que CLR deve ser executada quando a operação especificada expire.</span><span class="sxs-lookup"><span data-stu-id="6e30f-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="6e30f-111">Método SetDefaultAction</span><span class="sxs-lookup"><span data-stu-id="6e30f-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="6e30f-112">Especifica a ação de política que CLR deve ser executada quando ocorre a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="6e30f-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="6e30f-113">Método SetTimeout</span><span class="sxs-lookup"><span data-stu-id="6e30f-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="6e30f-114">Define um valor de tempo limite para a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="6e30f-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="6e30f-115">Método SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="6e30f-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="6e30f-116">Define um valor de tempo limite para a operação especificada e especifica a ação de política que CLR deve ser executada quando ocorre a operação.</span><span class="sxs-lookup"><span data-stu-id="6e30f-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="6e30f-117">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="6e30f-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="6e30f-118">Especifica o comportamento do CLR quando ocorre uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="6e30f-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e30f-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e30f-119">Requirements</span></span>  
 <span data-ttu-id="6e30f-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e30f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e30f-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e30f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e30f-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6e30f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e30f-123">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e30f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e30f-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e30f-124">See Also</span></span>  
 [<span data-ttu-id="6e30f-125">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="6e30f-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="6e30f-126">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="6e30f-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="6e30f-127">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="6e30f-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="6e30f-128">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="6e30f-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)

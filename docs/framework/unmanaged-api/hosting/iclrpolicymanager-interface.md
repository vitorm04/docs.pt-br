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
ms.openlocfilehash: 2eeccc4dfd7a7147fe791444eeeca2bd3a844305
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638860"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="6d988-102">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="6d988-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="6d988-103">Fornece métodos que permitem que o host especificar ações de política a ser executada no caso de falhas e tempos limite.</span><span class="sxs-lookup"><span data-stu-id="6d988-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d988-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6d988-104">Methods</span></span>  
  
|<span data-ttu-id="6d988-105">Método</span><span class="sxs-lookup"><span data-stu-id="6d988-105">Method</span></span>|<span data-ttu-id="6d988-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d988-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d988-107">Método SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="6d988-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="6d988-108">Especifica a ação de política, que o common language runtime (CLR) deve tomar quando ocorre a falha especificada.</span><span class="sxs-lookup"><span data-stu-id="6d988-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="6d988-109">Método SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="6d988-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="6d988-110">Especifica a ação de política, que o CLR deve tomar quando a operação especificada expira.</span><span class="sxs-lookup"><span data-stu-id="6d988-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="6d988-111">Método SetDefaultAction</span><span class="sxs-lookup"><span data-stu-id="6d988-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="6d988-112">Especifica a ação de política, que o CLR deve tomar quando ocorre a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="6d988-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="6d988-113">Método SetTimeout</span><span class="sxs-lookup"><span data-stu-id="6d988-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="6d988-114">Define um valor de tempo limite para a operação especificada.</span><span class="sxs-lookup"><span data-stu-id="6d988-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="6d988-115">Método SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="6d988-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="6d988-116">Define um valor de tempo limite para a operação especificada e especifica a ação de política, que o CLR deve tomar quando a operação ocorre.</span><span class="sxs-lookup"><span data-stu-id="6d988-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="6d988-117">Método SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="6d988-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="6d988-118">Especifica o comportamento do CLR quando ocorre uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="6d988-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d988-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d988-119">Requirements</span></span>  
 <span data-ttu-id="6d988-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d988-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d988-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d988-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d988-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6d988-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d988-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d988-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d988-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d988-124">See also</span></span>

- [<span data-ttu-id="6d988-125">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="6d988-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="6d988-126">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="6d988-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="6d988-127">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="6d988-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="6d988-128">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="6d988-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)

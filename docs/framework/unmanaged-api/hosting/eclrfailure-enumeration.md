---
title: "Enumeração EClrFailure"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrFailure
helpviewer_keywords: EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94358fd0626fa17f1fd6d3c365aff79f89dde467
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="087c7-102">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="087c7-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="087c7-103">Descreve o conjunto de falhas para o qual um host pode definir as ações de política.</span><span class="sxs-lookup"><span data-stu-id="087c7-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="087c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="087c7-104">Syntax</span></span>  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="087c7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="087c7-105">Members</span></span>  
  
|<span data-ttu-id="087c7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="087c7-106">Member</span></span>|<span data-ttu-id="087c7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="087c7-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="087c7-108">Ocorreu uma falha durante uma tentativa de alocar um recurso (como um segmento, um bloco de memória ou um bloqueio) em uma região não críticos do código.</span><span class="sxs-lookup"><span data-stu-id="087c7-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="087c7-109">Ocorreu uma falha durante uma tentativa de alocar um recurso (como um segmento, um bloco de memória ou um bloqueio) em uma região crítica de código.</span><span class="sxs-lookup"><span data-stu-id="087c7-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="087c7-110">O common language runtime (CLR) não é capaz de executar código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="087c7-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="087c7-111">Daqui em diante, as chamadas para as funções de hospedagem retornam um valor HRESULT HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="087c7-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="087c7-112">Um thread falhou ao liberar um bloqueio no retorno de uma <xref:System.AppDomain> objeto.</span><span class="sxs-lookup"><span data-stu-id="087c7-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="087c7-113">O host não é possível definir essa falha para fazer com que um thread anular.</span><span class="sxs-lookup"><span data-stu-id="087c7-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="087c7-114">Ocorreu um estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="087c7-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="087c7-115">Foi feita uma tentativa de leitura ou gravação em memória protegida.</span><span class="sxs-lookup"><span data-stu-id="087c7-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="087c7-116">Não há suportada no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="087c7-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="087c7-117">Ocorreu uma falha de contrato de código.</span><span class="sxs-lookup"><span data-stu-id="087c7-117">A code contract failure occurred.</span></span> <span data-ttu-id="087c7-118">Consulte [contratos de código](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="087c7-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="087c7-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="087c7-119">Remarks</span></span>  
 <span data-ttu-id="087c7-120">Consulte o [SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) método para obter uma lista de [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores host pode ser usados para especificar as ações de política para condições de falha.</span><span class="sxs-lookup"><span data-stu-id="087c7-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="087c7-121">Para obter mais informações sobre regiões não-críticas e de código, consulte [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="087c7-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="087c7-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="087c7-122">Requirements</span></span>  
 <span data-ttu-id="087c7-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="087c7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="087c7-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="087c7-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="087c7-125">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="087c7-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="087c7-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="087c7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="087c7-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="087c7-127">See Also</span></span>  
 [<span data-ttu-id="087c7-128">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="087c7-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="087c7-129">Método SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="087c7-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [<span data-ttu-id="087c7-130">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="087c7-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="087c7-131">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="087c7-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

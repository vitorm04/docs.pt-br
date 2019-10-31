---
title: Enumeração EClrFailure
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: 7d935bff023d806cf8cfb6d87bde0f82666b51b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131120"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="cf7ec-102">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="cf7ec-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="cf7ec-103">Descreve o conjunto de falhas para as quais um host pode definir ações de política.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf7ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf7ec-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="cf7ec-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cf7ec-105">Members</span></span>  
  
|<span data-ttu-id="cf7ec-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cf7ec-106">Member</span></span>|<span data-ttu-id="cf7ec-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf7ec-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="cf7ec-108">Ocorreu uma falha durante uma tentativa de alocar um recurso (como um thread, um bloco de memória ou um bloqueio) em uma região não crítica de código.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="cf7ec-109">Ocorreu uma falha durante uma tentativa de alocar um recurso (como um thread, um bloco de memória ou um bloqueio) em uma região crítica de código.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="cf7ec-110">O Common Language Runtime (CLR) não é mais capaz de executar código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="cf7ec-111">Daqui em diante, chamadas para qualquer função de hospedagem retornam um valor HRESULT de HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="cf7ec-112">Um thread não pôde liberar um bloqueio ao retornar de um objeto <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="cf7ec-113">O host não pode definir essa falha para fazer com que um thread seja anulado.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="cf7ec-114">Ocorreu um estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="cf7ec-115">Foi feita uma tentativa de ler ou gravar na memória protegida.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="cf7ec-116">Sem suporte no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="cf7ec-117">Ocorreu uma falha de contrato de código.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-117">A code contract failure occurred.</span></span> <span data-ttu-id="cf7ec-118">Consulte [contratos de código](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="cf7ec-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf7ec-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf7ec-119">Remarks</span></span>  
 <span data-ttu-id="cf7ec-120">Consulte o método [ICLRPolicyManager:: SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) para obter uma lista de valores [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) que o host pode usar para especificar as ações de política para condições de falha.</span><span class="sxs-lookup"><span data-stu-id="cf7ec-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="cf7ec-121">Para obter mais informações sobre regiões críticas e não críticas de código, consulte [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="cf7ec-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf7ec-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf7ec-122">Requirements</span></span>  
 <span data-ttu-id="cf7ec-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf7ec-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf7ec-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cf7ec-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf7ec-125">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cf7ec-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf7ec-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf7ec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf7ec-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf7ec-127">See also</span></span>

- [<span data-ttu-id="cf7ec-128">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="cf7ec-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="cf7ec-129">Método SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="cf7ec-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="cf7ec-130">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="cf7ec-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="cf7ec-131">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="cf7ec-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

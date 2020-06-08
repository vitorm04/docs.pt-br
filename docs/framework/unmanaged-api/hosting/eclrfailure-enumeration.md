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
ms.openlocfilehash: fa2b5052a1d569487f0c6c72699ff9ab571beefc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504388"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="1c25a-102">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="1c25a-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="1c25a-103">Descreve o conjunto de falhas para as quais um host pode definir ações de política.</span><span class="sxs-lookup"><span data-stu-id="1c25a-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c25a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c25a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1c25a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1c25a-105">Members</span></span>  
  
|<span data-ttu-id="1c25a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1c25a-106">Member</span></span>|<span data-ttu-id="1c25a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c25a-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="1c25a-108">Ocorreu uma falha durante uma tentativa de alocar um recurso (como um thread, um bloco de memória ou um bloqueio) em uma região não crítica de código.</span><span class="sxs-lookup"><span data-stu-id="1c25a-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="1c25a-109">Ocorreu uma falha durante uma tentativa de alocar um recurso (como um thread, um bloco de memória ou um bloqueio) em uma região crítica de código.</span><span class="sxs-lookup"><span data-stu-id="1c25a-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="1c25a-110">O Common Language Runtime (CLR) não é mais capaz de executar código gerenciado no processo.</span><span class="sxs-lookup"><span data-stu-id="1c25a-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="1c25a-111">Daqui em diante, chamadas para qualquer função de hospedagem retornam um valor HRESULT de HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1c25a-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="1c25a-112">Um thread não pôde liberar um bloqueio ao retornar de um <xref:System.AppDomain> objeto.</span><span class="sxs-lookup"><span data-stu-id="1c25a-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="1c25a-113">O host não pode definir essa falha para fazer com que um thread seja anulado.</span><span class="sxs-lookup"><span data-stu-id="1c25a-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="1c25a-114">Ocorreu um estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="1c25a-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="1c25a-115">Foi feita uma tentativa de ler ou gravar na memória protegida.</span><span class="sxs-lookup"><span data-stu-id="1c25a-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="1c25a-116">Sem suporte no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1c25a-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="1c25a-117">Ocorreu uma falha de contrato de código.</span><span class="sxs-lookup"><span data-stu-id="1c25a-117">A code contract failure occurred.</span></span> <span data-ttu-id="1c25a-118">Consulte [contratos de código](../../debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="1c25a-118">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c25a-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c25a-119">Remarks</span></span>  
 <span data-ttu-id="1c25a-120">Consulte o método [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) para obter uma lista de valores [EPolicyAction](epolicyaction-enumeration.md) que o host pode usar para especificar as ações de política para condições de falha.</span><span class="sxs-lookup"><span data-stu-id="1c25a-120">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="1c25a-121">Para obter mais informações sobre regiões críticas e não críticas de código, consulte [EClrOperation](eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="1c25a-121">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c25a-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c25a-122">Requirements</span></span>  
 <span data-ttu-id="1c25a-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c25a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c25a-124">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1c25a-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c25a-125">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1c25a-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c25a-126">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c25a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c25a-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="1c25a-127">See also</span></span>

- [<span data-ttu-id="1c25a-128">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="1c25a-128">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="1c25a-129">Método SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="1c25a-129">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="1c25a-130">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="1c25a-130">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="1c25a-131">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="1c25a-131">Hosting Enumerations</span></span>](hosting-enumerations.md)

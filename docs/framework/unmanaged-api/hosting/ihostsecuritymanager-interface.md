---
title: Interface IHostSecurityManager
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 237fe23493460df77a79ba3aed9f0a809cd8aa23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501463"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="3d1dd-102">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="3d1dd-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="3d1dd-103">Fornece métodos que permitem o acesso e o controle sobre o contexto de segurança do thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d1dd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3d1dd-104">Methods</span></span>  
  
|<span data-ttu-id="3d1dd-105">Método</span><span class="sxs-lookup"><span data-stu-id="3d1dd-105">Method</span></span>|<span data-ttu-id="3d1dd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d1dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d1dd-107">Método GetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="3d1dd-107">GetSecurityContext Method</span></span>](ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="3d1dd-108">Obtém o [IHostSecurityContext](ihostsecuritycontext-interface.md) solicitado do host.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-108">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="3d1dd-109">Método ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="3d1dd-109">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="3d1dd-110">Solicita que o código seja executado usando as credenciais da identidade do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="3d1dd-111">Método OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="3d1dd-111">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="3d1dd-112">Abre o token de acesso discricionário associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="3d1dd-113">Método RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="3d1dd-113">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="3d1dd-114">Encerra a representação da identidade do usuário atual e retorna o token do thread original.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="3d1dd-115">Método SetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="3d1dd-115">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="3d1dd-116">Define o contexto de segurança para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="3d1dd-117">Método SetThreadToken</span><span class="sxs-lookup"><span data-stu-id="3d1dd-117">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="3d1dd-118">Define um identificador para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d1dd-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d1dd-119">Remarks</span></span>  
 <span data-ttu-id="3d1dd-120">Um host pode controlar todo o acesso de código aos tokens de thread pelo Common Language Runtime (CLR) e pelo código do usuário.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="3d1dd-121">Ele também pode garantir que as informações completas do contexto de segurança sejam passadas entre operações assíncronas ou pontos de código com acesso restrito ao código.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="3d1dd-122">`IHostSecurityContext`encapsula essas informações de contexto de segurança, que são opacas para o CLR.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="3d1dd-123">O CLR lida internamente com o contexto de thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="3d1dd-124">Ele consulta o processo específico `IHostSecurityManager` nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="3d1dd-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="3d1dd-125">No thread do finalizador, durante a execução do finalizador.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="3d1dd-126">Durante a execução do construtor de classes e módulos.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="3d1dd-127">Em pontos assíncronos no thread de trabalho, em chamadas para o método [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3d1dd-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="3d1dd-128">Em serviços de portas de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d1dd-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d1dd-129">Requirements</span></span>  
 <span data-ttu-id="3d1dd-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d1dd-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d1dd-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3d1dd-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d1dd-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3d1dd-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d1dd-133">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d1dd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1dd-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="3d1dd-134">See also</span></span>

- [<span data-ttu-id="3d1dd-135">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="3d1dd-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="3d1dd-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="3d1dd-136">Hosting Interfaces</span></span>](hosting-interfaces.md)

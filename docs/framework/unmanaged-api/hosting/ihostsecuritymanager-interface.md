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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45379fe8640ef7e7b3917bac8d10ca956d75ffb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223752"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="852f0-102">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="852f0-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="852f0-103">Fornece métodos que permitem acesso e controle sobre o contexto de segurança do thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="852f0-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="852f0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="852f0-104">Methods</span></span>  
  
|<span data-ttu-id="852f0-105">Método</span><span class="sxs-lookup"><span data-stu-id="852f0-105">Method</span></span>|<span data-ttu-id="852f0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="852f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="852f0-107">Método GetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="852f0-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="852f0-108">Obtém o solicitada [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) do host.</span><span class="sxs-lookup"><span data-stu-id="852f0-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="852f0-109">Método ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="852f0-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="852f0-110">As solicitações que o código ser executado usando as credenciais da identidade do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="852f0-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="852f0-111">Método OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="852f0-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="852f0-112">Abre o token de acesso discricionário associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="852f0-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="852f0-113">Método RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="852f0-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="852f0-114">Finaliza a representação da identidade do usuário atual e retorna o token do thread original.</span><span class="sxs-lookup"><span data-stu-id="852f0-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="852f0-115">Método SetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="852f0-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="852f0-116">Define o contexto de segurança para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="852f0-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="852f0-117">Método SetThreadToken</span><span class="sxs-lookup"><span data-stu-id="852f0-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="852f0-118">Define um identificador para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="852f0-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="852f0-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="852f0-119">Remarks</span></span>  
 <span data-ttu-id="852f0-120">Um host pode controlar todo o acesso de código para tokens de thread, o common language runtime (CLR) e o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="852f0-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="852f0-121">Ele também pode garantir que a segurança completa informações de contexto são passadas entre os pontos de código com acesso de código restrito ou operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="852f0-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="852f0-122">`IHostSecurityContext` encapsula a essas informações de contexto de segurança, que é opacas para o CLR.</span><span class="sxs-lookup"><span data-stu-id="852f0-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="852f0-123">O CLR trata o contexto de thread gerenciado internamente.</span><span class="sxs-lookup"><span data-stu-id="852f0-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="852f0-124">Ele consulta o processo específico `IHostSecurityManager` nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="852f0-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="852f0-125">No thread do finalizador, durante a execução do finalizador.</span><span class="sxs-lookup"><span data-stu-id="852f0-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="852f0-126">Durante a execução de construtor de classe e módulo.</span><span class="sxs-lookup"><span data-stu-id="852f0-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="852f0-127">Em pontos assíncronos no thread de trabalho, em chamadas para o [ihostthreadpoolmanager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="852f0-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="852f0-128">Na manutenção das portas de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="852f0-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="852f0-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="852f0-129">Requirements</span></span>  
 <span data-ttu-id="852f0-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="852f0-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="852f0-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="852f0-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="852f0-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="852f0-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="852f0-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="852f0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852f0-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="852f0-134">See also</span></span>

- [<span data-ttu-id="852f0-135">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="852f0-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="852f0-136">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="852f0-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

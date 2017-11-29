---
title: Interface IHostSecurityManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager
helpviewer_keywords: IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b3d67328dbf68491d319e55e63a9c3540cd1ee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="af2f7-102">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="af2f7-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="af2f7-103">Fornece métodos que permitem o acesso e controle sobre o contexto de segurança do thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="af2f7-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af2f7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="af2f7-104">Methods</span></span>  
  
|<span data-ttu-id="af2f7-105">Método</span><span class="sxs-lookup"><span data-stu-id="af2f7-105">Method</span></span>|<span data-ttu-id="af2f7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="af2f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af2f7-107">Método GetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="af2f7-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="af2f7-108">Obtém a solicitação [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) do host.</span><span class="sxs-lookup"><span data-stu-id="af2f7-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="af2f7-109">Método ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="af2f7-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="af2f7-110">Solicitações que código ser executado usando as credenciais da identidade do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="af2f7-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="af2f7-111">Método OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="af2f7-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="af2f7-112">Abre o token de acesso discricionário associado ao segmento atual.</span><span class="sxs-lookup"><span data-stu-id="af2f7-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="af2f7-113">Método RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="af2f7-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="af2f7-114">Finaliza a representação da identidade do usuário atual e retorna o token de thread original.</span><span class="sxs-lookup"><span data-stu-id="af2f7-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="af2f7-115">Método SetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="af2f7-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="af2f7-116">Define o contexto de segurança para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="af2f7-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="af2f7-117">Método SetThreadToken</span><span class="sxs-lookup"><span data-stu-id="af2f7-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="af2f7-118">Define um identificador para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="af2f7-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af2f7-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="af2f7-119">Remarks</span></span>  
 <span data-ttu-id="af2f7-120">Um host pode controlar o acesso de código todos os tokens de thread, o common language runtime (CLR) e o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="af2f7-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="af2f7-121">Ele também pode assegurar que a segurança completa informações de contexto são passadas pela operações assíncronas ou pontos de código com acesso restrito de código.</span><span class="sxs-lookup"><span data-stu-id="af2f7-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="af2f7-122">`IHostSecurityContext`encapsula essas informações de contexto de segurança, que é opacas para o CLR.</span><span class="sxs-lookup"><span data-stu-id="af2f7-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="af2f7-123">O CLR trata o contexto do thread gerenciado internamente.</span><span class="sxs-lookup"><span data-stu-id="af2f7-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="af2f7-124">Ele consulta o específicos de processo `IHostSecurityManager` nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="af2f7-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="af2f7-125">No thread do finalizador, durante a execução do finalizador.</span><span class="sxs-lookup"><span data-stu-id="af2f7-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="af2f7-126">Durante a execução de construtor de classe e o módulo.</span><span class="sxs-lookup"><span data-stu-id="af2f7-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="af2f7-127">Em pontos assíncronos no thread de trabalho, em chamadas para o [Ihostthreadpoolmanager](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="af2f7-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="af2f7-128">Serviço de portas de conclusão de e/s.</span><span class="sxs-lookup"><span data-stu-id="af2f7-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af2f7-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af2f7-129">Requirements</span></span>  
 <span data-ttu-id="af2f7-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af2f7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af2f7-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="af2f7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af2f7-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="af2f7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af2f7-133">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af2f7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2f7-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af2f7-134">See Also</span></span>  
 [<span data-ttu-id="af2f7-135">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="af2f7-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="af2f7-136">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="af2f7-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

---
title: Interface IHostSecurityContext
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityContext
helpviewer_keywords: IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1d3c616ced761b696f50e9207e6fad312f06c31c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="7e2e0-102">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="7e2e0-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="7e2e0-103">Permite que o common language runtime (CLR) para manter informações de contexto de segurança implementadas pelo host.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e2e0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7e2e0-104">Methods</span></span>  
  
|<span data-ttu-id="7e2e0-105">Método</span><span class="sxs-lookup"><span data-stu-id="7e2e0-105">Method</span></span>|<span data-ttu-id="7e2e0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e2e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e2e0-107">Método Capture</span><span class="sxs-lookup"><span data-stu-id="7e2e0-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="7e2e0-108">Obtém um clone do `IHostSecurityContext` instância retornada de uma chamada para [Ihostsecuritymanager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e2e0-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e2e0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e2e0-109">Remarks</span></span>  
 <span data-ttu-id="7e2e0-110">Um host pode controlar o acesso de código de todos os tokens de thread pelo código do usuário e o CLR.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="7e2e0-111">Ele também pode assegurar que a segurança completa informações de contexto são passadas pela operações assíncronas ou pontos de código com acesso restrito de código.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="7e2e0-112">`IHostSecurityContext`encapsula essas informações de contexto de segurança, que é opacas para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="7e2e0-113">O runtime captura essas informações usando `Capture`, e move-lo ao longo de expedição de item de trabalho de pool de thread, a execução do finalizador e construtores de classe e de módulo.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e2e0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e2e0-114">Requirements</span></span>  
 <span data-ttu-id="7e2e0-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e2e0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e2e0-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e2e0-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e2e0-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7e2e0-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e2e0-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e2e0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2e0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e2e0-119">See Also</span></span>  
 [<span data-ttu-id="7e2e0-120">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="7e2e0-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="7e2e0-121">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="7e2e0-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="7e2e0-122">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="7e2e0-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

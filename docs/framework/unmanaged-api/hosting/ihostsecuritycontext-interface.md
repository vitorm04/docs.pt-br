---
title: Interface IHostSecurityContext
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984289"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="f4cb3-102">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="f4cb3-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="f4cb3-103">Permite que o common language runtime (CLR) para manter informações de contexto de segurança implementadas pelo host.</span><span class="sxs-lookup"><span data-stu-id="f4cb3-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4cb3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f4cb3-104">Methods</span></span>  
  
|<span data-ttu-id="f4cb3-105">Método</span><span class="sxs-lookup"><span data-stu-id="f4cb3-105">Method</span></span>|<span data-ttu-id="f4cb3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4cb3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4cb3-107">Método Capture</span><span class="sxs-lookup"><span data-stu-id="f4cb3-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="f4cb3-108">Obtém um clone do `IHostSecurityContext` instância retornada de uma chamada para [ihostsecuritymanager:: Getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="f4cb3-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4cb3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4cb3-109">Remarks</span></span>  
 <span data-ttu-id="f4cb3-110">Um host pode controlar todo o acesso de código para tokens de thread pelo código do usuário e o CLR.</span><span class="sxs-lookup"><span data-stu-id="f4cb3-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="f4cb3-111">Ele também pode garantir que a segurança completa informações de contexto são passadas entre os pontos de código com acesso de código restrito ou operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="f4cb3-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="f4cb3-112">`IHostSecurityContext` encapsula a essas informações de contexto de segurança, que é opacas para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f4cb3-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="f4cb3-113">O tempo de execução captura essas informações usando `Capture`, e a move entre despacho de item de trabalho de pool de threads, execução do finalizador e construtores de classe e de módulo.</span><span class="sxs-lookup"><span data-stu-id="f4cb3-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4cb3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4cb3-114">Requirements</span></span>  
 <span data-ttu-id="f4cb3-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4cb3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4cb3-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4cb3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4cb3-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f4cb3-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4cb3-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4cb3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4cb3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4cb3-119">See also</span></span>

- [<span data-ttu-id="f4cb3-120">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="f4cb3-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="f4cb3-121">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="f4cb3-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="f4cb3-122">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="f4cb3-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

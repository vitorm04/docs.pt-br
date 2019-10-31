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
ms.openlocfilehash: 993d16818b25dfefe1f53c7afd06bc9857d9eb24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121516"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="20e9a-102">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="20e9a-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="20e9a-103">Permite que o Common Language Runtime (CLR) Mantenha informações de contexto de segurança implementadas pelo host.</span><span class="sxs-lookup"><span data-stu-id="20e9a-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20e9a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="20e9a-104">Methods</span></span>  
  
|<span data-ttu-id="20e9a-105">Método</span><span class="sxs-lookup"><span data-stu-id="20e9a-105">Method</span></span>|<span data-ttu-id="20e9a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="20e9a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20e9a-107">Método Capture</span><span class="sxs-lookup"><span data-stu-id="20e9a-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="20e9a-108">Obtém um clone da instância de `IHostSecurityContext` retornada de uma chamada para [IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="20e9a-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20e9a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="20e9a-109">Remarks</span></span>  
 <span data-ttu-id="20e9a-110">Um host pode controlar todo o acesso ao código para tokens de thread tanto pelo CLR quanto pelo código do usuário.</span><span class="sxs-lookup"><span data-stu-id="20e9a-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="20e9a-111">Ele também pode garantir que as informações completas do contexto de segurança sejam passadas entre operações assíncronas ou pontos de código com acesso restrito ao código.</span><span class="sxs-lookup"><span data-stu-id="20e9a-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="20e9a-112">`IHostSecurityContext` encapsula essas informações de contexto de segurança, que são opacas para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="20e9a-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="20e9a-113">O tempo de execução captura essas informações usando `Capture`e as move entre a expedição do item de trabalho do pool de threads, a execução do finalizador e os construtores de módulo e classe.</span><span class="sxs-lookup"><span data-stu-id="20e9a-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e9a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20e9a-114">Requirements</span></span>  
 <span data-ttu-id="20e9a-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20e9a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e9a-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20e9a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20e9a-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20e9a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20e9a-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e9a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e9a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20e9a-119">See also</span></span>

- [<span data-ttu-id="20e9a-120">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="20e9a-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="20e9a-121">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="20e9a-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="20e9a-122">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="20e9a-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

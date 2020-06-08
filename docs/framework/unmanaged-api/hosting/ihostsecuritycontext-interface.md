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
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501489"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="ba50c-102">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="ba50c-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="ba50c-103">Permite que o Common Language Runtime (CLR) Mantenha informações de contexto de segurança implementadas pelo host.</span><span class="sxs-lookup"><span data-stu-id="ba50c-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba50c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ba50c-104">Methods</span></span>  
  
|<span data-ttu-id="ba50c-105">Método</span><span class="sxs-lookup"><span data-stu-id="ba50c-105">Method</span></span>|<span data-ttu-id="ba50c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba50c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba50c-107">Método Capture</span><span class="sxs-lookup"><span data-stu-id="ba50c-107">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="ba50c-108">Obtém um clone da `IHostSecurityContext` instância retornada de uma chamada para [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="ba50c-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba50c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba50c-109">Remarks</span></span>  
 <span data-ttu-id="ba50c-110">Um host pode controlar todo o acesso ao código para tokens de thread tanto pelo CLR quanto pelo código do usuário.</span><span class="sxs-lookup"><span data-stu-id="ba50c-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="ba50c-111">Ele também pode garantir que as informações completas do contexto de segurança sejam passadas entre operações assíncronas ou pontos de código com acesso restrito ao código.</span><span class="sxs-lookup"><span data-stu-id="ba50c-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="ba50c-112">`IHostSecurityContext`encapsula essas informações de contexto de segurança, que são opacas para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ba50c-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="ba50c-113">O tempo de execução captura essas informações usando o `Capture` e move-as entre a expedição do item de trabalho do pool de threads, a execução do finalizador e os construtores de módulo e classe.</span><span class="sxs-lookup"><span data-stu-id="ba50c-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba50c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba50c-114">Requirements</span></span>  
 <span data-ttu-id="ba50c-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba50c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba50c-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ba50c-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba50c-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ba50c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba50c-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba50c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba50c-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="ba50c-119">See also</span></span>

- [<span data-ttu-id="ba50c-120">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="ba50c-120">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="ba50c-121">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="ba50c-121">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="ba50c-122">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="ba50c-122">Hosting Interfaces</span></span>](hosting-interfaces.md)

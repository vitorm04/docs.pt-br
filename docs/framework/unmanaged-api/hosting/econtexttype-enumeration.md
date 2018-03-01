---
title: "Enumeração EContextType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd068816c5a642a7a8230fc14045e3f43980936c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="ece95-102">Enumeração EContextType</span><span class="sxs-lookup"><span data-stu-id="ece95-102">EContextType Enumeration</span></span>
<span data-ttu-id="ece95-103">Descreve o contexto de segurança do thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="ece95-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece95-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ece95-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="ece95-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ece95-105">Members</span></span>  
  
|<span data-ttu-id="ece95-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ece95-106">Member</span></span>|<span data-ttu-id="ece95-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ece95-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="ece95-108">Indica o contexto no thread atual no momento em que o common language runtime (CLR) chama o [Ihostsecuritymanager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) método ou o contexto solicitado pelo CLR em uma chamada para o [ Ihostsecuritymanager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ece95-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="ece95-109">Indica um contexto em que o host tem privilégios mais baixos, como o coletor de lixo ou construtores de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="ece95-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ece95-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ece95-110">Remarks</span></span>  
 <span data-ttu-id="ece95-111">O CLR fornece uma da `EContextType` valores como um valor de parâmetro em chamadas para o `IHostSecurityManager::GetSecurityContext` e `IHostSecurityManager::SetSecurityContext` métodos.</span><span class="sxs-lookup"><span data-stu-id="ece95-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ece95-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ece95-112">Requirements</span></span>  
 <span data-ttu-id="ece95-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ece95-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ece95-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ece95-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ece95-115">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ece95-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ece95-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ece95-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece95-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ece95-117">See Also</span></span>  
 [<span data-ttu-id="ece95-118">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="ece95-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="ece95-119">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="ece95-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="ece95-120">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="ece95-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

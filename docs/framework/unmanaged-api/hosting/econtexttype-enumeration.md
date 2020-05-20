---
title: Enumeração EContextType
ms.date: 03/30/2017
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
ms.openlocfilehash: ceb68410e808bf7843149e3f05a39c7a98d0c000
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616288"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="1388d-102">Enumeração EContextType</span><span class="sxs-lookup"><span data-stu-id="1388d-102">EContextType Enumeration</span></span>
<span data-ttu-id="1388d-103">Descreve o contexto de segurança do thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="1388d-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1388d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1388d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="1388d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1388d-105">Members</span></span>  
  
|<span data-ttu-id="1388d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1388d-106">Member</span></span>|<span data-ttu-id="1388d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1388d-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="1388d-108">Indica o contexto no thread atual no momento em que o Common Language Runtime (CLR) chama o método [IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) ou o contexto solicitado pelo CLR em uma chamada para o método [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1388d-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="1388d-109">Indica um contexto sobre o qual o host tem privilégios mais baixos, como o coletor de lixo ou construtores de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="1388d-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1388d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1388d-110">Remarks</span></span>  
 <span data-ttu-id="1388d-111">O CLR fornece um dos `EContextType` valores como um valor de parâmetro em chamadas para os `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` métodos e.</span><span class="sxs-lookup"><span data-stu-id="1388d-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1388d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1388d-112">Requirements</span></span>  
 <span data-ttu-id="1388d-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1388d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1388d-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1388d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1388d-115">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1388d-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1388d-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1388d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1388d-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="1388d-117">See also</span></span>

- [<span data-ttu-id="1388d-118">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="1388d-118">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="1388d-119">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="1388d-119">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="1388d-120">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="1388d-120">Hosting Enumerations</span></span>](hosting-enumerations.md)

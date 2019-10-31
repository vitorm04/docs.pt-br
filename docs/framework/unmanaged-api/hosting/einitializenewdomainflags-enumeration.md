---
title: Enumeração EInitializeNewDomainFlags
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 3693285e13d0650f7662e2187471027cc4c40704
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129414"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="dc76c-102">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="dc76c-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="dc76c-103">Permite que o host forneça o tempo de execução com informações sobre a inicialização de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc76c-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc76c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc76c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="dc76c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dc76c-105">Members</span></span>  
  
|<span data-ttu-id="dc76c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dc76c-106">Member</span></span>|<span data-ttu-id="dc76c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc76c-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="dc76c-108">Sem sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="dc76c-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="dc76c-109">Informa ao Common Language Runtime (CLR) que o host não fará alterações no estado de segurança do domínio do aplicativo no método <xref:System.AppDomainManager.InitializeNewDomain%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc76c-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc76c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc76c-110">Remarks</span></span>  
 <span data-ttu-id="dc76c-111">O método [ICLRDomainManager:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) usa um parâmetro do tipo `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="dc76c-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc76c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc76c-112">Requirements</span></span>  
 <span data-ttu-id="dc76c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc76c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc76c-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dc76c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc76c-115">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dc76c-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc76c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc76c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc76c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc76c-117">See also</span></span>

- [<span data-ttu-id="dc76c-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="dc76c-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="dc76c-119">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="dc76c-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)

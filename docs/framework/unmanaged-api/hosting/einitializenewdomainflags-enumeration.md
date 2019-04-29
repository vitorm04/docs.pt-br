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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04b0d9989d66888c33de0359e4c93529fcfbf8d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628620"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="47bcc-102">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="47bcc-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="47bcc-103">Permite que o host fornecer o tempo de execução com informações sobre a inicialização de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47bcc-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47bcc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47bcc-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="47bcc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="47bcc-105">Members</span></span>  
  
|<span data-ttu-id="47bcc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="47bcc-106">Member</span></span>|<span data-ttu-id="47bcc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="47bcc-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="47bcc-108">Sem sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="47bcc-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="47bcc-109">Informa o common language runtime (CLR) que o host não fará alterações para o estado de segurança do domínio do aplicativo na <xref:System.AppDomainManager.InitializeNewDomain%2A> método.</span><span class="sxs-lookup"><span data-stu-id="47bcc-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47bcc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="47bcc-110">Remarks</span></span>  
 <span data-ttu-id="47bcc-111">O [iclrdomainmanager:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) método utiliza um parâmetro de tipo `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="47bcc-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47bcc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47bcc-112">Requirements</span></span>  
 <span data-ttu-id="47bcc-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47bcc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47bcc-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47bcc-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47bcc-115">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47bcc-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47bcc-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47bcc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47bcc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47bcc-117">See also</span></span>

- [<span data-ttu-id="47bcc-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="47bcc-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="47bcc-119">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="47bcc-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)

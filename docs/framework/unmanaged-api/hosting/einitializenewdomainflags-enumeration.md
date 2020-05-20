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
ms.openlocfilehash: 7ff10f84d8d270d31c5d560fb3c9bd3c81cf3e24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616223"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="80f01-102">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="80f01-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="80f01-103">Permite que o host forneça o tempo de execução com informações sobre a inicialização de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80f01-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80f01-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80f01-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="80f01-105">Membros</span><span class="sxs-lookup"><span data-stu-id="80f01-105">Members</span></span>  
  
|<span data-ttu-id="80f01-106">Membro</span><span class="sxs-lookup"><span data-stu-id="80f01-106">Member</span></span>|<span data-ttu-id="80f01-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="80f01-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="80f01-108">Sem sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="80f01-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="80f01-109">Informa ao Common Language Runtime (CLR) que o host não fará alterações no estado de segurança do domínio do aplicativo no <xref:System.AppDomainManager.InitializeNewDomain%2A> método.</span><span class="sxs-lookup"><span data-stu-id="80f01-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80f01-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="80f01-110">Remarks</span></span>  
 <span data-ttu-id="80f01-111">O método [ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) usa um parâmetro do tipo `EInitializeNewDomainFlags` .</span><span class="sxs-lookup"><span data-stu-id="80f01-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80f01-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80f01-112">Requirements</span></span>  
 <span data-ttu-id="80f01-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80f01-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80f01-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80f01-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80f01-115">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80f01-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80f01-116">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80f01-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f01-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="80f01-117">See also</span></span>

- [<span data-ttu-id="80f01-118">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="80f01-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="80f01-119">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="80f01-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)

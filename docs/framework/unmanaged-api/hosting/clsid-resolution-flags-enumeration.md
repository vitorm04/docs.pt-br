---
title: Enumeração CLSID_RESOLUTION_FLAGS
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36792d01ebdad72271a8b0597a33d83cab34780e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789578"
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="901a1-102">Enumeração CLSID_RESOLUTION_FLAGS</span><span class="sxs-lookup"><span data-stu-id="901a1-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="901a1-103">Contém valores que indicam como o common language runtime (CLR) deve resolver uma `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="901a1-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="901a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="901a1-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="901a1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="901a1-105">Members</span></span>  
  
|<span data-ttu-id="901a1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="901a1-106">Member</span></span>|<span data-ttu-id="901a1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="901a1-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="901a1-108">Indica o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="901a1-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="901a1-109">Indica que o tempo de execução procura o registro e aplica a política de correção.</span><span class="sxs-lookup"><span data-stu-id="901a1-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="901a1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="901a1-110">Requirements</span></span>  
 <span data-ttu-id="901a1-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="901a1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="901a1-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="901a1-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="901a1-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="901a1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="901a1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="901a1-114">See also</span></span>

- [<span data-ttu-id="901a1-115">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="901a1-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

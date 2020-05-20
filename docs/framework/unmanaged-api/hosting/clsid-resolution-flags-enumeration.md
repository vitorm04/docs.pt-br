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
ms.openlocfilehash: 5ac015f958d9504bbd14a66ead86548b8df32764
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616769"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="e862c-102">Enumeração CLSID_RESOLUTION_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e862c-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="e862c-103">Contém valores que indicam como o Common Language Runtime (CLR) deve resolver um `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="e862c-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e862c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e862c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e862c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e862c-105">Members</span></span>  
  
|<span data-ttu-id="e862c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e862c-106">Member</span></span>|<span data-ttu-id="e862c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e862c-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="e862c-108">Indica o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="e862c-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="e862c-109">Indica que o tempo de execução pesquisa o registro e aplica a política Shim.</span><span class="sxs-lookup"><span data-stu-id="e862c-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e862c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e862c-110">Requirements</span></span>  
 <span data-ttu-id="e862c-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e862c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e862c-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e862c-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e862c-113">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e862c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e862c-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="e862c-114">See also</span></span>

- [<span data-ttu-id="e862c-115">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="e862c-115">Hosting Enumerations</span></span>](hosting-enumerations.md)

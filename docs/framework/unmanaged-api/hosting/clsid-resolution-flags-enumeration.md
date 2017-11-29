---
title: "Enumeração CLSID_RESOLUTION_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLSID_RESOLUTION_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: CLSID_RESOLUTION_FLAGS
helpviewer_keywords: CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17e74e8b39ff9079973063f4ea703607411ab93d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="d9f24-102">Enumeração CLSID_RESOLUTION_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d9f24-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="d9f24-103">Contém valores que indicam como o common language runtime (CLR) deve resolver uma `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="d9f24-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9f24-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="d9f24-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d9f24-105">Members</span></span>  
  
|<span data-ttu-id="d9f24-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d9f24-106">Member</span></span>|<span data-ttu-id="d9f24-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9f24-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="d9f24-108">Indica o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="d9f24-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="d9f24-109">Indica que o tempo de execução procura o registro e aplica a política de correção.</span><span class="sxs-lookup"><span data-stu-id="d9f24-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9f24-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9f24-110">Requirements</span></span>  
 <span data-ttu-id="d9f24-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9f24-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9f24-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9f24-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9f24-113">**Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9f24-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f24-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9f24-114">See Also</span></span>  
 [<span data-ttu-id="d9f24-115">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d9f24-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

---
title: Enumeração MALLOC_TYPE
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 695f69c8d9c3a295a705971743733339cf8aab13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211940"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="cabe8-102">Enumeração MALLOC_TYPE</span><span class="sxs-lookup"><span data-stu-id="cabe8-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="cabe8-103">Contém valores que especificam as características da memória que está sendo alocada.</span><span class="sxs-lookup"><span data-stu-id="cabe8-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cabe8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cabe8-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="cabe8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cabe8-105">Members</span></span>  
  
|<span data-ttu-id="cabe8-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cabe8-106">Member</span></span>|<span data-ttu-id="cabe8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cabe8-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="cabe8-108">A memória alocada pode conter um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="cabe8-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="cabe8-109">A memória alocada é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="cabe8-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="cabe8-110">Ou seja, a memória pode ser acessada por vários threads sem qualquer sincronização.</span><span class="sxs-lookup"><span data-stu-id="cabe8-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="cabe8-111">Se este sinalizador não for definido, chamadas no objeto devem ser serializadas.</span><span class="sxs-lookup"><span data-stu-id="cabe8-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cabe8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cabe8-112">Requirements</span></span>  
 <span data-ttu-id="cabe8-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cabe8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cabe8-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cabe8-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cabe8-115">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cabe8-115">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cabe8-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cabe8-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cabe8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cabe8-117">See also</span></span>

- [<span data-ttu-id="cabe8-118">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="cabe8-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765213"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="149e5-102">Enumeração MALLOC_TYPE</span><span class="sxs-lookup"><span data-stu-id="149e5-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="149e5-103">Contém valores que especificam as características da memória que está sendo alocada.</span><span class="sxs-lookup"><span data-stu-id="149e5-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="149e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="149e5-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="149e5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="149e5-105">Members</span></span>  
  
|<span data-ttu-id="149e5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="149e5-106">Member</span></span>|<span data-ttu-id="149e5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="149e5-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="149e5-108">A memória alocada pode conter um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="149e5-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="149e5-109">A memória alocada é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="149e5-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="149e5-110">Ou seja, a memória pode ser acessada por vários threads sem qualquer sincronização.</span><span class="sxs-lookup"><span data-stu-id="149e5-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="149e5-111">Se este sinalizador não for definido, chamadas no objeto devem ser serializadas.</span><span class="sxs-lookup"><span data-stu-id="149e5-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="149e5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="149e5-112">Requirements</span></span>  
 <span data-ttu-id="149e5-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="149e5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="149e5-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="149e5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="149e5-115">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="149e5-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="149e5-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="149e5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="149e5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="149e5-117">See also</span></span>

- [<span data-ttu-id="149e5-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="149e5-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

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
ms.openlocfilehash: f1c3fd9155761528b9203a5c69dee0bde16327f7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779345"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="6de1f-102">Enumeração MALLOC_TYPE</span><span class="sxs-lookup"><span data-stu-id="6de1f-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="6de1f-103">Contém valores que especificam as características da memória que está sendo alocada.</span><span class="sxs-lookup"><span data-stu-id="6de1f-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de1f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6de1f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="6de1f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6de1f-105">Members</span></span>  
  
|<span data-ttu-id="6de1f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6de1f-106">Member</span></span>|<span data-ttu-id="6de1f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6de1f-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="6de1f-108">A memória alocada pode conter um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="6de1f-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="6de1f-109">A memória alocada é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="6de1f-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="6de1f-110">Ou seja, a memória pode ser acessada por vários threads sem qualquer sincronização.</span><span class="sxs-lookup"><span data-stu-id="6de1f-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="6de1f-111">Se este sinalizador não for definido, chamadas no objeto devem ser serializadas.</span><span class="sxs-lookup"><span data-stu-id="6de1f-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6de1f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6de1f-112">Requirements</span></span>  
 <span data-ttu-id="6de1f-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de1f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de1f-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6de1f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6de1f-115">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6de1f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6de1f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de1f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de1f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6de1f-117">See also</span></span>

- [<span data-ttu-id="6de1f-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="6de1f-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

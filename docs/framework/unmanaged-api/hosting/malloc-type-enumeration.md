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
ms.openlocfilehash: 16f56809b4db159c71b06b3bb9d969f8a8f8fc54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090829"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="fe11c-102">Enumeração MALLOC_TYPE</span><span class="sxs-lookup"><span data-stu-id="fe11c-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="fe11c-103">Contém valores que especificam as características da memória que está sendo alocada.</span><span class="sxs-lookup"><span data-stu-id="fe11c-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe11c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe11c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="fe11c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fe11c-105">Members</span></span>  
  
|<span data-ttu-id="fe11c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fe11c-106">Member</span></span>|<span data-ttu-id="fe11c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe11c-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="fe11c-108">A memória alocada pode conter um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="fe11c-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="fe11c-109">A memória alocada é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="fe11c-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="fe11c-110">Ou seja, a memória pode ser acessada por vários threads sem nenhuma sincronização.</span><span class="sxs-lookup"><span data-stu-id="fe11c-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="fe11c-111">Se esse sinalizador não for definido, as chamadas no objeto deverão ser serializadas.</span><span class="sxs-lookup"><span data-stu-id="fe11c-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe11c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe11c-112">Requirements</span></span>  
 <span data-ttu-id="fe11c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe11c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe11c-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fe11c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe11c-115">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fe11c-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe11c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe11c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe11c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe11c-117">See also</span></span>

- [<span data-ttu-id="fe11c-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="fe11c-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

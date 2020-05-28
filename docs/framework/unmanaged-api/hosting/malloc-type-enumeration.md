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
ms.openlocfilehash: 630fe4e79b369bfdefc19be72780f1893090895e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008450"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="9a9f0-102">Enumeração MALLOC_TYPE</span><span class="sxs-lookup"><span data-stu-id="9a9f0-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="9a9f0-103">Contém valores que especificam as características da memória que está sendo alocada.</span><span class="sxs-lookup"><span data-stu-id="9a9f0-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a9f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a9f0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="9a9f0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9a9f0-105">Members</span></span>  
  
|<span data-ttu-id="9a9f0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9a9f0-106">Member</span></span>|<span data-ttu-id="9a9f0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a9f0-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="9a9f0-108">A memória alocada pode conter um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="9a9f0-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="9a9f0-109">A memória alocada é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="9a9f0-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="9a9f0-110">Ou seja, a memória pode ser acessada por vários threads sem nenhuma sincronização.</span><span class="sxs-lookup"><span data-stu-id="9a9f0-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="9a9f0-111">Se esse sinalizador não for definido, as chamadas no objeto deverão ser serializadas.</span><span class="sxs-lookup"><span data-stu-id="9a9f0-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a9f0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a9f0-112">Requirements</span></span>  
 <span data-ttu-id="9a9f0-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a9f0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a9f0-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a9f0-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a9f0-115">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a9f0-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a9f0-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a9f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a9f0-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a9f0-117">See also</span></span>

- [<span data-ttu-id="9a9f0-118">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="9a9f0-118">Hosting Enumerations</span></span>](hosting-enumerations.md)

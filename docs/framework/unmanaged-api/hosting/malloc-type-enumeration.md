---
title: "Enumeração MALLOC_TYPE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MALLOC_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: MALLOC_TYPE
helpviewer_keywords: MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59a379b1c34f5b7c6b721627e6053cacf3ed784a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="317b7-102">Enumeração MALLOC_TYPE</span><span class="sxs-lookup"><span data-stu-id="317b7-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="317b7-103">Contém valores que especificam as características da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="317b7-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="317b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="317b7-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="317b7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="317b7-105">Members</span></span>  
  
|<span data-ttu-id="317b7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="317b7-106">Member</span></span>|<span data-ttu-id="317b7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="317b7-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="317b7-108">A memória alocada pode conter um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="317b7-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="317b7-109">A memória alocada é thread-safe.</span><span class="sxs-lookup"><span data-stu-id="317b7-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="317b7-110">Ou seja, a memória pode ser acessada por vários threads sem qualquer sincronização.</span><span class="sxs-lookup"><span data-stu-id="317b7-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="317b7-111">Se este sinalizador não for definido, as chamadas no objeto devem ser serializadas.</span><span class="sxs-lookup"><span data-stu-id="317b7-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="317b7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="317b7-112">Requirements</span></span>  
 <span data-ttu-id="317b7-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="317b7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="317b7-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="317b7-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="317b7-115">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="317b7-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="317b7-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="317b7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="317b7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="317b7-117">See Also</span></span>  
 [<span data-ttu-id="317b7-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="317b7-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

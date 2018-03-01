---
title: "Enumeração CorSaveSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3780050285f63fa7334ec5463cd22050836dc136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="caa29-102">Enumeração CorSaveSize</span><span class="sxs-lookup"><span data-stu-id="caa29-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="caa29-103">Contém valores que indica o nível de precisão necessária ao consultar o tamanho de um salvamento operação.</span><span class="sxs-lookup"><span data-stu-id="caa29-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="caa29-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="caa29-105">Membros</span><span class="sxs-lookup"><span data-stu-id="caa29-105">Members</span></span>  
  
|<span data-ttu-id="caa29-106">Membro</span><span class="sxs-lookup"><span data-stu-id="caa29-106">Member</span></span>|<span data-ttu-id="caa29-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="caa29-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="caa29-108">Especifica que o valor de retorno deve ser exato.</span><span class="sxs-lookup"><span data-stu-id="caa29-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="caa29-109">Especifica que o valor de retorno deve ser estimado.</span><span class="sxs-lookup"><span data-stu-id="caa29-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="caa29-110">Especifica que tipos descartáveis devem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="caa29-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="caa29-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="caa29-111">Requirements</span></span>  
 <span data-ttu-id="caa29-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caa29-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa29-113">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="caa29-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="caa29-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="caa29-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="caa29-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa29-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa29-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="caa29-116">See Also</span></span>  
 [<span data-ttu-id="caa29-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="caa29-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

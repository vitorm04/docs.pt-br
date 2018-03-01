---
title: "Enumeração AssemblyRefFlags"
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
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0a749a2f0016e7f2ea22c1d61c82f25ac78a9b9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="f6c2d-102">Enumeração AssemblyRefFlags</span><span class="sxs-lookup"><span data-stu-id="f6c2d-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="f6c2d-103">Contém valores que descrevem os recursos de uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="f6c2d-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c2d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6c2d-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f6c2d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f6c2d-105">Members</span></span>  
  
|<span data-ttu-id="f6c2d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f6c2d-106">Member</span></span>|<span data-ttu-id="f6c2d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6c2d-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="f6c2d-108">Especifica que a referência de assembly contém completas, sem hash informações sobre o Editor do assembly.</span><span class="sxs-lookup"><span data-stu-id="f6c2d-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6c2d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6c2d-109">Requirements</span></span>  
 <span data-ttu-id="f6c2d-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6c2d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6c2d-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6c2d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6c2d-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6c2d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c2d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6c2d-113">See Also</span></span>  
 [<span data-ttu-id="f6c2d-114">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="f6c2d-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="f6c2d-115">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="f6c2d-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="f6c2d-116">Método DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="f6c2d-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)

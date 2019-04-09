---
title: Enumeração AssemblyRefFlags
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc98b2421d23ffd6dfb716a8cc782b46a9d59ce0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128889"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="b7e38-102">Enumeração AssemblyRefFlags</span><span class="sxs-lookup"><span data-stu-id="b7e38-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="b7e38-103">Contém valores que descrevem os recursos de uma referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="b7e38-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7e38-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b7e38-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b7e38-105">Members</span></span>  
  
|<span data-ttu-id="b7e38-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b7e38-106">Member</span></span>|<span data-ttu-id="b7e38-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e38-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="b7e38-108">Especifica que a referência do assembly contém completas, sem hash informações sobre o Editor do assembly.</span><span class="sxs-lookup"><span data-stu-id="b7e38-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7e38-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7e38-109">Requirements</span></span>  
 <span data-ttu-id="b7e38-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7e38-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7e38-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b7e38-111">**Header:** Cor.h</span></span>  
  
 **<span data-ttu-id="b7e38-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b7e38-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b7e38-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7e38-113">See also</span></span>

- [<span data-ttu-id="b7e38-114">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="b7e38-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="b7e38-115">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="b7e38-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="b7e38-116">Método DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="b7e38-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)

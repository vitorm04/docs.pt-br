---
title: "Enumeração CorFileFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileFlags
helpviewer_keywords: CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf123f734f73ecfe726a80099de6ec06b0ced06b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="eb58c-102">Enumeração CorFileFlags</span><span class="sxs-lookup"><span data-stu-id="eb58c-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="eb58c-103">Contém valores que descrevem o tipo de arquivo definido em uma chamada para [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="eb58c-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb58c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb58c-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="eb58c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="eb58c-105">Members</span></span>  
  
|<span data-ttu-id="eb58c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="eb58c-106">Member</span></span>|<span data-ttu-id="eb58c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb58c-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="eb58c-108">Indica que o arquivo não é um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="eb58c-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="eb58c-109">Indica que o arquivo, possivelmente, um arquivo de recurso, não contém metadados.</span><span class="sxs-lookup"><span data-stu-id="eb58c-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb58c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb58c-110">Requirements</span></span>  
 <span data-ttu-id="eb58c-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb58c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb58c-112">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="eb58c-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eb58c-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb58c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb58c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb58c-114">See Also</span></span>  
 [<span data-ttu-id="eb58c-115">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="eb58c-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

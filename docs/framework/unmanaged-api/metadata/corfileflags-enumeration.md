---
title: Enumeração CorFileFlags
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 076d5de3e9d1925e3a030fee4a06a89862105897
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159608"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="22bef-102">Enumeração CorFileFlags</span><span class="sxs-lookup"><span data-stu-id="22bef-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="22bef-103">Contém valores que descrevem o tipo de arquivo definido em uma chamada para [imetadataassemblyemit:: Definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="22bef-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22bef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22bef-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="22bef-105">Membros</span><span class="sxs-lookup"><span data-stu-id="22bef-105">Members</span></span>  
  
|<span data-ttu-id="22bef-106">Membro</span><span class="sxs-lookup"><span data-stu-id="22bef-106">Member</span></span>|<span data-ttu-id="22bef-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="22bef-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="22bef-108">Indica que o arquivo não é um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="22bef-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="22bef-109">Indica que o arquivo, possivelmente, um arquivo de recurso, não contém metadados.</span><span class="sxs-lookup"><span data-stu-id="22bef-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22bef-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22bef-110">Requirements</span></span>  
 <span data-ttu-id="22bef-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22bef-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22bef-112">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="22bef-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="22bef-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22bef-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22bef-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22bef-114">See also</span></span>

- [<span data-ttu-id="22bef-115">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="22bef-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

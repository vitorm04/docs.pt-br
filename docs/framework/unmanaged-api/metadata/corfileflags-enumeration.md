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
ms.openlocfilehash: c8c2757e99b80204ad52e69a596d62c55c369965
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007410"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="dd7bd-102">Enumeração CorFileFlags</span><span class="sxs-lookup"><span data-stu-id="dd7bd-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="dd7bd-103">Contém valores que descrevem o tipo de arquivo definido em uma chamada para [IMetaDataAssemblyEmit::D efinefile](imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="dd7bd-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd7bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd7bd-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="dd7bd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dd7bd-105">Members</span></span>  
  
|<span data-ttu-id="dd7bd-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dd7bd-106">Member</span></span>|<span data-ttu-id="dd7bd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd7bd-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="dd7bd-108">Indica que o arquivo não é um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="dd7bd-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="dd7bd-109">Indica que o arquivo, possivelmente um arquivo de recurso, não contém metadados.</span><span class="sxs-lookup"><span data-stu-id="dd7bd-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd7bd-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd7bd-110">Requirements</span></span>  
 <span data-ttu-id="dd7bd-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd7bd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd7bd-112">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="dd7bd-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dd7bd-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd7bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7bd-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd7bd-114">See also</span></span>

- [<span data-ttu-id="dd7bd-115">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="dd7bd-115">Metadata Enumerations</span></span>](metadata-enumerations.md)

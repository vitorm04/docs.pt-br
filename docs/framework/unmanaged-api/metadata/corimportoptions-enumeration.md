---
title: Enumeração CorImportOptions
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38c0937804eb82d1c96a605b55a00784ba58fe13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781823"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="44a66-102">Enumeração CorImportOptions</span><span class="sxs-lookup"><span data-stu-id="44a66-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="44a66-103">Contém valores de sinalizadores que controlam o comportamento durante a importação de um assembly fora do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="44a66-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44a66-104">Syntax</span></span>  
  
```cpp  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="44a66-105">Membros</span><span class="sxs-lookup"><span data-stu-id="44a66-105">Members</span></span>  
  
|<span data-ttu-id="44a66-106">Membro</span><span class="sxs-lookup"><span data-stu-id="44a66-106">Member</span></span>|<span data-ttu-id="44a66-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="44a66-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="44a66-108">Indica o comportamento padrão, que é ignorar registros excluídos.</span><span class="sxs-lookup"><span data-stu-id="44a66-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="44a66-109">Indica que todos os metadados devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="44a66-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="44a66-110">Indica que todas as definições de tipo, incluindo o que foi excluído, devem ser enumeradas.</span><span class="sxs-lookup"><span data-stu-id="44a66-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="44a66-111">Indica que todos os MethodDefs, incluindo o que foi excluído, deve ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="44a66-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="44a66-112">Indica que todos os FieldDefs, incluindo o que foi excluído, deve ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="44a66-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="44a66-113">Indica que todos os PropertyDefs, incluindo o que foi excluído, deve ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="44a66-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="44a66-114">Indica que todos os EventDefs, incluindo o que foi excluído, deve ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="44a66-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="44a66-115">Indica que todos os atributos personalizados, incluindo o que foi excluído, devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="44a66-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="44a66-116">Indica que todos os tipos exportados, incluindo o que foi excluído, devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="44a66-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44a66-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44a66-117">Requirements</span></span>  
 <span data-ttu-id="44a66-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44a66-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44a66-119">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="44a66-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="44a66-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44a66-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a66-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44a66-121">See also</span></span>

- [<span data-ttu-id="44a66-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="44a66-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

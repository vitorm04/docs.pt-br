---
title: "Enumeração CorImportOptions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorImportOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorImportOptions
helpviewer_keywords: CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e014443945574cff2733e5bc5d992691acc3fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="9cb43-102">Enumeração CorImportOptions</span><span class="sxs-lookup"><span data-stu-id="9cb43-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="9cb43-103">Contém valores de sinalizadores que controlam o comportamento durante a importação de um assembly fora do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="9cb43-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9cb43-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="9cb43-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9cb43-105">Members</span></span>  
  
|<span data-ttu-id="9cb43-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9cb43-106">Member</span></span>|<span data-ttu-id="9cb43-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cb43-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="9cb43-108">Indica o comportamento padrão, que é ignorar os registros excluídos.</span><span class="sxs-lookup"><span data-stu-id="9cb43-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="9cb43-109">Indica que todos os metadados devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9cb43-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="9cb43-110">Indica que todas as definições de tipo, incluindo aquelas excluído, devem ser enumeradas.</span><span class="sxs-lookup"><span data-stu-id="9cb43-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="9cb43-111">Indica que todos os MethodDefs, incluindo aquelas excluído, deve ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9cb43-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="9cb43-112">Indica que todos os FieldDefs, incluindo aquelas excluído, deve ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9cb43-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="9cb43-113">Indica que todos os PropertyDefs, incluindo aquelas excluído, deve ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9cb43-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="9cb43-114">Indica que todos os EventDefs, incluindo aquelas excluído, deve ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9cb43-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="9cb43-115">Indica que todos os atributos personalizados, incluindo aquelas excluído, devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9cb43-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="9cb43-116">Indica que todos os tipos exportados, incluindo aquelas excluído, devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="9cb43-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9cb43-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9cb43-117">Requirements</span></span>  
 <span data-ttu-id="9cb43-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cb43-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb43-119">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="9cb43-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9cb43-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb43-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb43-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cb43-121">See Also</span></span>  
 [<span data-ttu-id="9cb43-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="9cb43-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

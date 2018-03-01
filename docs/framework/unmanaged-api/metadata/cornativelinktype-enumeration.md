---
title: "Enumeração CorNativeLinkType"
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
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f19a4366958249881c1f4c33919f239f33c21b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="903d1-102">Enumeração CorNativeLinkType</span><span class="sxs-lookup"><span data-stu-id="903d1-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="903d1-103">Fornece valores que indicam o tipo vinculado em código nativo.</span><span class="sxs-lookup"><span data-stu-id="903d1-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="903d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="903d1-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="903d1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="903d1-105">Members</span></span>  
  
|<span data-ttu-id="903d1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="903d1-106">Member</span></span>|<span data-ttu-id="903d1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="903d1-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="903d1-108">Indica que nenhuma das palavras-chave são especificadas.</span><span class="sxs-lookup"><span data-stu-id="903d1-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="903d1-109">Indica que uma palavra-chave ANSI é especificada.</span><span class="sxs-lookup"><span data-stu-id="903d1-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="903d1-110">Indica que uma palavra-chave Unicode foi especificada</span><span class="sxs-lookup"><span data-stu-id="903d1-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="903d1-111">Indica que uma palavra-chave auto é especificada.</span><span class="sxs-lookup"><span data-stu-id="903d1-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="903d1-112">Indica que uma palavra-chave OLE é especificada.</span><span class="sxs-lookup"><span data-stu-id="903d1-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="903d1-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="903d1-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="903d1-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="903d1-114">Requirements</span></span>  
 <span data-ttu-id="903d1-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="903d1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="903d1-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="903d1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="903d1-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="903d1-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="903d1-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="903d1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="903d1-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="903d1-119">See Also</span></span>  
 [<span data-ttu-id="903d1-120">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="903d1-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

---
title: Enumeração CorNotificationForTokenMovement
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15c5e8b34f2748868611bd7dc47ef73c491b1338
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045429"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="5c2be-102">Enumeração CorNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="5c2be-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="5c2be-103">Especifica as notificações que serão enviadas para o cliente da API de metadados quando ocorre um remapeamento do token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c2be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c2be-104">Syntax</span></span>  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="5c2be-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5c2be-105">Members</span></span>  
  
|<span data-ttu-id="5c2be-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5c2be-106">Member</span></span>|<span data-ttu-id="5c2be-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c2be-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="5c2be-108">Notificar quando `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, ou `mdFieldDef` movimentação de tokens.</span><span class="sxs-lookup"><span data-stu-id="5c2be-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="5c2be-109">Notificar quando qualquer token move.</span><span class="sxs-lookup"><span data-stu-id="5c2be-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="5c2be-110">Notifica quando mover de tokens.</span><span class="sxs-lookup"><span data-stu-id="5c2be-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="5c2be-111">Notificar quando um `mdMethodDef` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="5c2be-112">Notificar quando um `mdMemberRef` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="5c2be-113">Notificar quando um `mdFieldDef` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="5c2be-114">Notificar quando um `mdTypeRef` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="5c2be-115">Notificar quando um `mdTypeDef` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="5c2be-116">Notificar quando um `mdParamDef` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="5c2be-117">Notificar quando um `mdInterfaceImpl` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="5c2be-118">Notificar quando um `mdProperty` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="5c2be-119">Notificar quando um `mdEvent` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="5c2be-120">Notificar quando um `mdSignature` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="5c2be-121">Notificar quando um `mdTypeSpec` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="5c2be-122">Notificar quando um `mdCustomAttribute` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="5c2be-123">Notificar quando um `mdSecurityValue` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="5c2be-124">Notificar quando um `mdPermission` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="5c2be-125">Notificar quando um `mdModuleRef` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="5c2be-126">Notificar quando um `mdNameSpace` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="5c2be-127">Notificar quando um `mdAssemblyRef` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="5c2be-128">Notificar quando um `mdFile` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="5c2be-129">Notificar quando um `mdExportedType` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="5c2be-130">Notificar quando um `mdManifestResource` movimentações de token.</span><span class="sxs-lookup"><span data-stu-id="5c2be-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c2be-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c2be-131">Remarks</span></span>  
 <span data-ttu-id="5c2be-132">Um token pode ser novamente mapeado (que é, movido) durante uma mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="5c2be-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c2be-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c2be-133">Requirements</span></span>  
 <span data-ttu-id="5c2be-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c2be-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c2be-135">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5c2be-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5c2be-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c2be-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c2be-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c2be-137">See also</span></span>

- [<span data-ttu-id="5c2be-138">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="5c2be-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

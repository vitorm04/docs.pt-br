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
ms.openlocfilehash: 96ab659e6ab6cc9601c0e9a1ab511da92905c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448250"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="06822-102">Enumeração CorNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="06822-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="06822-103">Especifica as notificações serão enviadas para o cliente de API de metadados quando um token remapeamento ocorre.</span><span class="sxs-lookup"><span data-stu-id="06822-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06822-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06822-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="06822-105">Membros</span><span class="sxs-lookup"><span data-stu-id="06822-105">Members</span></span>  
  
|<span data-ttu-id="06822-106">Membro</span><span class="sxs-lookup"><span data-stu-id="06822-106">Member</span></span>|<span data-ttu-id="06822-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="06822-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="06822-108">Notificar quando `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, ou `mdFieldDef` movimentação de tokens.</span><span class="sxs-lookup"><span data-stu-id="06822-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="06822-109">Notificar quando qualquer token move.</span><span class="sxs-lookup"><span data-stu-id="06822-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="06822-110">Não notifica quando mover tokens.</span><span class="sxs-lookup"><span data-stu-id="06822-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="06822-111">Notificar quando um `mdMethodDef` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="06822-112">Notificar quando um `mdMemberRef` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="06822-113">Notificar quando um `mdFieldDef` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="06822-114">Notificar quando um `mdTypeRef` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="06822-115">Notificar quando um `mdTypeDef` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="06822-116">Notificar quando um `mdParamDef` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="06822-117">Notificar quando um `mdInterfaceImpl` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="06822-118">Notificar quando um `mdProperty` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="06822-119">Notificar quando um `mdEvent` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="06822-120">Notificar quando um `mdSignature` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="06822-121">Notificar quando um `mdTypeSpec` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="06822-122">Notificar quando um `mdCustomAttribute` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="06822-123">Notificar quando um `mdSecurityValue` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="06822-124">Notificar quando um `mdPermission` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="06822-125">Notificar quando um `mdModuleRef` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="06822-126">Notificar quando um `mdNameSpace` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="06822-127">Notificar quando um `mdAssemblyRef` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="06822-128">Notificar quando um `mdFile` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="06822-129">Notificar quando um `mdExportedType` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="06822-130">Notificar quando um `mdManifestResource` move de token.</span><span class="sxs-lookup"><span data-stu-id="06822-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06822-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="06822-131">Remarks</span></span>  
 <span data-ttu-id="06822-132">Um token pode ser novamente mapeado (que é, movidos) durante a mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="06822-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06822-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06822-133">Requirements</span></span>  
 <span data-ttu-id="06822-134">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06822-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06822-135">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="06822-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="06822-136">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06822-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06822-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06822-137">See Also</span></span>  
 [<span data-ttu-id="06822-138">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="06822-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

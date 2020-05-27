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
ms.openlocfilehash: e8065a5492884a4b7f5d662737e4beddc6fca5b3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007592"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="7c56e-102">Enumeração CorNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="7c56e-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="7c56e-103">Especifica as notificações que serão enviadas para o cliente da API de metadados quando ocorrer um remapeamento de token.</span><span class="sxs-lookup"><span data-stu-id="7c56e-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c56e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c56e-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="7c56e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7c56e-105">Members</span></span>  
  
|<span data-ttu-id="7c56e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7c56e-106">Member</span></span>|<span data-ttu-id="7c56e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c56e-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="7c56e-108">Notifique quando `mdTypeRef` os `mdMethodDef` `mdMemberRef` `mdFieldDef` tokens são movidos.</span><span class="sxs-lookup"><span data-stu-id="7c56e-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="7c56e-109">Notificar quando qualquer token for movido.</span><span class="sxs-lookup"><span data-stu-id="7c56e-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="7c56e-110">Não notificar quando os tokens forem movidos.</span><span class="sxs-lookup"><span data-stu-id="7c56e-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="7c56e-111">Notificar quando um `mdMethodDef` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="7c56e-112">Notificar quando um `mdMemberRef` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="7c56e-113">Notificar quando um `mdFieldDef` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="7c56e-114">Notificar quando um `mdTypeRef` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="7c56e-115">Notificar quando um `mdTypeDef` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="7c56e-116">Notificar quando um `mdParamDef` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="7c56e-117">Notificar quando um `mdInterfaceImpl` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="7c56e-118">Notificar quando um `mdProperty` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="7c56e-119">Notificar quando um `mdEvent` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="7c56e-120">Notificar quando um `mdSignature` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="7c56e-121">Notificar quando um `mdTypeSpec` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="7c56e-122">Notificar quando um `mdCustomAttribute` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="7c56e-123">Notificar quando um `mdSecurityValue` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="7c56e-124">Notificar quando um `mdPermission` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="7c56e-125">Notificar quando um `mdModuleRef` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="7c56e-126">Notificar quando um `mdNameSpace` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="7c56e-127">Notificar quando um `mdAssemblyRef` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="7c56e-128">Notificar quando um `mdFile` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="7c56e-129">Notificar quando um `mdExportedType` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="7c56e-130">Notificar quando um `mdManifestResource` token se mover.</span><span class="sxs-lookup"><span data-stu-id="7c56e-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c56e-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c56e-131">Remarks</span></span>  
 <span data-ttu-id="7c56e-132">Um token pode ser mapeado novamente (ou seja, movido) durante uma mesclagem de metadados.</span><span class="sxs-lookup"><span data-stu-id="7c56e-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c56e-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c56e-133">Requirements</span></span>  
 <span data-ttu-id="7c56e-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c56e-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c56e-135">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="7c56e-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7c56e-136">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c56e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c56e-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="7c56e-137">See also</span></span>

- [<span data-ttu-id="7c56e-138">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="7c56e-138">Metadata Enumerations</span></span>](metadata-enumerations.md)

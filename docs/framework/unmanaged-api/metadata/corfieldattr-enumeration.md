---
title: Enumeração CorFieldAttr
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: d28a0c8b7ee85f023026dde6f3cc8f3a8406aa64
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450308"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="30086-102">Enumeração CorFieldAttr</span><span class="sxs-lookup"><span data-stu-id="30086-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="30086-103">Contains values that describe metadata about a field.</span><span class="sxs-lookup"><span data-stu-id="30086-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30086-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30086-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="30086-105">Membros</span><span class="sxs-lookup"><span data-stu-id="30086-105">Members</span></span>  
  
|<span data-ttu-id="30086-106">Membro</span><span class="sxs-lookup"><span data-stu-id="30086-106">Member</span></span>|<span data-ttu-id="30086-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="30086-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="30086-108">Specifies accessibility information.</span><span class="sxs-lookup"><span data-stu-id="30086-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="30086-109">Especifica que o campo não pode ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="30086-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="30086-110">Specifies that the field is accessible only by its parent type.</span><span class="sxs-lookup"><span data-stu-id="30086-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="30086-111">Specifies that the field is accessible by derived classes in its assembly.</span><span class="sxs-lookup"><span data-stu-id="30086-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="30086-112">Specifies that the field is accessible by all types in its assembly.</span><span class="sxs-lookup"><span data-stu-id="30086-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="30086-113">Specifies that the field is accessible only by its type and derived classes.</span><span class="sxs-lookup"><span data-stu-id="30086-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="30086-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span><span class="sxs-lookup"><span data-stu-id="30086-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="30086-115">Specifies that the field is accessible by all types with visibility of this scope.</span><span class="sxs-lookup"><span data-stu-id="30086-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="30086-116">Specifies that the field is a member of its type rather than an instance member.</span><span class="sxs-lookup"><span data-stu-id="30086-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="30086-117">Specifies that the field cannot be changed after it is initialized.</span><span class="sxs-lookup"><span data-stu-id="30086-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="30086-118">Specifies that the field value is a compile-time constant.</span><span class="sxs-lookup"><span data-stu-id="30086-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="30086-119">Specifies that the field is not serialized when its type is remoted.</span><span class="sxs-lookup"><span data-stu-id="30086-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="30086-120">Specifies that the field is special, and that its name describes how.</span><span class="sxs-lookup"><span data-stu-id="30086-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="30086-121">Specifies that the field implementation is forwarded through PInvoke.</span><span class="sxs-lookup"><span data-stu-id="30086-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="30086-122">Reserved for internal use by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="30086-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="30086-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span><span class="sxs-lookup"><span data-stu-id="30086-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="30086-124">Specifies that the field contains marshaling information.</span><span class="sxs-lookup"><span data-stu-id="30086-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="30086-125">Especifica que o campo tem um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="30086-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="30086-126">Specifies that the field has a relative virtual address.</span><span class="sxs-lookup"><span data-stu-id="30086-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30086-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30086-127">Requirements</span></span>  
 <span data-ttu-id="30086-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30086-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30086-129">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="30086-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="30086-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30086-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30086-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30086-131">See also</span></span>

- [<span data-ttu-id="30086-132">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="30086-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

---
title: Enumeração CorCheckDuplicatesFor
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176182"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="9bdf6-102">Enumeração CorCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="9bdf6-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="9bdf6-103">Especifica os tokens de metadados que serão verificados para duplicatas.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bdf6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bdf6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="9bdf6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9bdf6-105">Members</span></span>  
  
|<span data-ttu-id="9bdf6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9bdf6-106">Member</span></span>|<span data-ttu-id="9bdf6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bdf6-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="9bdf6-108">Verifique todos os tokens de metadados para duplicatas.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="9bdf6-109">Não usado.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="9bdf6-110">Não verifique os tokens de metadados para duplicatas.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="9bdf6-111">Verifique se há `mdTypeDef` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="9bdf6-112">Verifique se há `mdInterfaceImpl` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="9bdf6-113">Verifique se há `mdMethodDef` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="9bdf6-114">Verifique se há `mdTypeRef` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="9bdf6-115">Verifique se há `mdMemberRef` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="9bdf6-116">Verifique se há `mdCustomAttribute` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="9bdf6-117">Verifique se há `mdParamDef` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="9bdf6-118">Verifique se há `mdPermission` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="9bdf6-119">Verifique se há `mdProperty` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="9bdf6-120">Verifique se há `mdEvent` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="9bdf6-121">Verifique se há `mdFieldDef` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="9bdf6-122">Verifique se há `mdSignature` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="9bdf6-123">Verifique se há `mdModuleRef` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="9bdf6-124">Verifique se há `mdTypeSpec` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="9bdf6-125">Verifique se há `mdImplMap` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="9bdf6-126">Verifique se há `mdAssemblyRef` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="9bdf6-127">Verifique se há `mdFile` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="9bdf6-128">Verifique se há `mdExportedType` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="9bdf6-129">Verifique se há `mdManifestResource` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="9bdf6-130">Verifique se há `mdGenericParam` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="9bdf6-131">Verifique se há `mdMethodSpec` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="9bdf6-132">Verifique se há `mdGenericParamConstraint` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="9bdf6-133">Verifique se há `mdAssembly` duplicatas de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="9bdf6-134">Verifique se há `mdMemberRef` `mdTypeRef`duplicatas de , `mdSignature`, e `mdTypeSpec` `mdMethodSpec` tokens.</span><span class="sxs-lookup"><span data-stu-id="9bdf6-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bdf6-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bdf6-135">Requirements</span></span>  
 <span data-ttu-id="9bdf6-136">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bdf6-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bdf6-137">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9bdf6-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9bdf6-138">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bdf6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bdf6-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="9bdf6-139">See also</span></span>

- [<span data-ttu-id="9bdf6-140">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="9bdf6-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

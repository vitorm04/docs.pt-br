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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cdb1570b682088e92ff7c7a78d84259d02d8512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="bc824-102">Enumeração CorCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="bc824-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="bc824-103">Especifica os tokens de metadados que serão verificados para duplicatas.</span><span class="sxs-lookup"><span data-stu-id="bc824-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc824-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc824-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="bc824-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bc824-105">Members</span></span>  
  
|<span data-ttu-id="bc824-106">Membro</span><span class="sxs-lookup"><span data-stu-id="bc824-106">Member</span></span>|<span data-ttu-id="bc824-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc824-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="bc824-108">Verifique se todos os tokens de metadados de duplicatas.</span><span class="sxs-lookup"><span data-stu-id="bc824-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="bc824-109">Não usado.</span><span class="sxs-lookup"><span data-stu-id="bc824-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="bc824-110">Não verifica tokens de metadados de duplicatas.</span><span class="sxs-lookup"><span data-stu-id="bc824-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="bc824-111">Verificar se há duplicatas de `mdTypeDef` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="bc824-112">Verificar se há duplicatas de `mdInterfaceImpl` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="bc824-113">Verificar se há duplicatas de `mdMethodDef` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="bc824-114">Verificar se há duplicatas de `mdTypeRef` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="bc824-115">Verificar se há duplicatas de `mdMemberRef` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="bc824-116">Verificar se há duplicatas de `mdCustomAttribute` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="bc824-117">Verificar se há duplicatas de `mdParamDef` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="bc824-118">Verificar se há duplicatas de `mdPermission` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="bc824-119">Verificar se há duplicatas de `mdProperty` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="bc824-120">Verificar se há duplicatas de `mdEvent` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="bc824-121">Verificar se há duplicatas de `mdFieldDef` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="bc824-122">Verificar se há duplicatas de `mdSignature` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="bc824-123">Verificar se há duplicatas de `mdModuleRef` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="bc824-124">Verificar se há duplicatas de `mdTypeSpec` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="bc824-125">Verificar se há duplicatas de `mdImplMap` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="bc824-126">Verificar se há duplicatas de `mdAssemblyRef` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="bc824-127">Verificar se há duplicatas de `mdFile` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="bc824-128">Verificar se há duplicatas de `mdExportedType` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="bc824-129">Verificar se há duplicatas de `mdManifestResource` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="bc824-130">Verificar se há duplicatas de `mdGenericParam` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="bc824-131">Verificar se há duplicatas de `mdMethodSpec` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="bc824-132">Verificar se há duplicatas de `mdGenericParamConstraint` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="bc824-133">Verificar se há duplicatas de `mdAssembly` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="bc824-134">Verificar se há duplicatas de `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, e `mdMethodSpec` tokens.</span><span class="sxs-lookup"><span data-stu-id="bc824-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc824-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc824-135">Requirements</span></span>  
 <span data-ttu-id="bc824-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc824-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc824-137">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="bc824-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bc824-138">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc824-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc824-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc824-139">See Also</span></span>  
 [<span data-ttu-id="bc824-140">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="bc824-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

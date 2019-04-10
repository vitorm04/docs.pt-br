---
title: Enumeração CorTokenType
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b33b50e53c454f2b62253d12943ea044240d8cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230506"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="e7c8b-102">Enumeração CorTokenType</span><span class="sxs-lookup"><span data-stu-id="e7c8b-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="e7c8b-103">Indica o tipo de um token de metadados.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7c8b-104">Syntax</span></span>  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="e7c8b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e7c8b-105">Members</span></span>  
  
|<span data-ttu-id="e7c8b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e7c8b-106">Member</span></span>|<span data-ttu-id="e7c8b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7c8b-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="e7c8b-108">Um `mdModule` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="e7c8b-109">Um `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="e7c8b-110">Um `mdTypeDef` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="e7c8b-111">Um `mdFieldDef` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="e7c8b-112">Um `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="e7c8b-113">Um `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="e7c8b-114">Um `mdInterfaceImpl` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="e7c8b-115">Um `mdMemberRef` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="e7c8b-116">Um `mdCustomAttribute` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="e7c8b-117">Um `mdPermission` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="e7c8b-118">Um `mdSignature` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="e7c8b-119">Um `mdEvent` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="e7c8b-120">Um `mdProperty` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="e7c8b-121">Um `mdModuleRef` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="e7c8b-122">Um `mdTypeSpec` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="e7c8b-123">Um `mdAssembly` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="e7c8b-124">Um `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="e7c8b-125">Um `mdFile` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="e7c8b-126">Um `mdExportedType` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="e7c8b-127">Um `mdManifestResource` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="e7c8b-128">Um `mdGenericParam` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="e7c8b-129">Um `mdMethodSpec` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="e7c8b-130">Um `mdGenericParamConstraint` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="e7c8b-131">Um `mdString` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="e7c8b-132">Um `mdName` token.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="e7c8b-133">Não usado.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7c8b-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7c8b-134">Remarks</span></span>  
 <span data-ttu-id="e7c8b-135">Cada valor é igual ao valor do byte superior no token de metadados correspondente.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7c8b-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7c8b-136">Requirements</span></span>  
 <span data-ttu-id="e7c8b-137">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7c8b-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7c8b-138">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e7c8b-138">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="e7c8b-139">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e7c8b-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e7c8b-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7c8b-140">See also</span></span>

- [<span data-ttu-id="e7c8b-141">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="e7c8b-141">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

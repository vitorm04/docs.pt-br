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
ms.openlocfilehash: 74807a678b5c0c2738f33fe552f6462af93ca1f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436457"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="25572-102">Enumeração CorTokenType</span><span class="sxs-lookup"><span data-stu-id="25572-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="25572-103">Indica o tipo de um token de metadados.</span><span class="sxs-lookup"><span data-stu-id="25572-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25572-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25572-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="25572-105">Membros</span><span class="sxs-lookup"><span data-stu-id="25572-105">Members</span></span>  
  
|<span data-ttu-id="25572-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="25572-106">Member</span></span>|<span data-ttu-id="25572-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="25572-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="25572-108">Um token `mdModule`.</span><span class="sxs-lookup"><span data-stu-id="25572-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="25572-109">Um token `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="25572-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="25572-110">Um token `mdTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="25572-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="25572-111">Um token `mdFieldDef`.</span><span class="sxs-lookup"><span data-stu-id="25572-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="25572-112">Um token `mdMethodDef`.</span><span class="sxs-lookup"><span data-stu-id="25572-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="25572-113">Um token `mdParamDef`.</span><span class="sxs-lookup"><span data-stu-id="25572-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="25572-114">Um token `mdInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="25572-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="25572-115">Um token `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="25572-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="25572-116">Um token `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="25572-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="25572-117">Um token `mdPermission`.</span><span class="sxs-lookup"><span data-stu-id="25572-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="25572-118">Um token `mdSignature`.</span><span class="sxs-lookup"><span data-stu-id="25572-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="25572-119">Um token `mdEvent`.</span><span class="sxs-lookup"><span data-stu-id="25572-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="25572-120">Um token `mdProperty`.</span><span class="sxs-lookup"><span data-stu-id="25572-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="25572-121">Um token `mdModuleRef`.</span><span class="sxs-lookup"><span data-stu-id="25572-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="25572-122">Um token `mdTypeSpec`.</span><span class="sxs-lookup"><span data-stu-id="25572-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="25572-123">Um token `mdAssembly`.</span><span class="sxs-lookup"><span data-stu-id="25572-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="25572-124">Um token `mdAssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="25572-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="25572-125">Um token `mdFile`.</span><span class="sxs-lookup"><span data-stu-id="25572-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="25572-126">Um token `mdExportedType`.</span><span class="sxs-lookup"><span data-stu-id="25572-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="25572-127">Um token `mdManifestResource`.</span><span class="sxs-lookup"><span data-stu-id="25572-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="25572-128">Um token `mdGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="25572-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="25572-129">Um token `mdMethodSpec`.</span><span class="sxs-lookup"><span data-stu-id="25572-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="25572-130">Um token `mdGenericParamConstraint`.</span><span class="sxs-lookup"><span data-stu-id="25572-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="25572-131">Um token `mdString`.</span><span class="sxs-lookup"><span data-stu-id="25572-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="25572-132">Um token `mdName`.</span><span class="sxs-lookup"><span data-stu-id="25572-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="25572-133">Não usado.</span><span class="sxs-lookup"><span data-stu-id="25572-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25572-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="25572-134">Remarks</span></span>  
 <span data-ttu-id="25572-135">Cada valor é igual ao valor do byte superior no token de metadados correspondente.</span><span class="sxs-lookup"><span data-stu-id="25572-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25572-136">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="25572-136">Requirements</span></span>  
 <span data-ttu-id="25572-137">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25572-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25572-138">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="25572-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="25572-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25572-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25572-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25572-140">See also</span></span>

- [<span data-ttu-id="25572-141">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="25572-141">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

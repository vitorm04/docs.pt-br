---
title: "Método IMetaDataAssemblyEmit::SetManifestResourceProps"
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
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6649b8f82031699692a0929b5483ba57147399b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="1b4ed-102">Método IMetaDataAssemblyEmit::SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="1b4ed-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="1b4ed-103">Modifica especificado `ManifestResource` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="1b4ed-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b4ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b4ed-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b4ed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b4ed-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="1b4ed-106">[in] O token que especifica o `ManifestResource` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="1b4ed-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="1b4ed-107">[in] O token, do tipo `File` ou `AssemblyRef`, que é mapeado para o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="1b4ed-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="1b4ed-108">[in] O deslocamento para o início do recurso dentro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="1b4ed-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="1b4ed-109">[in] Uma combinação bit a bit de valores de sinalizador que especifica os atributos do recurso.</span><span class="sxs-lookup"><span data-stu-id="1b4ed-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b4ed-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b4ed-110">Remarks</span></span>  
 <span data-ttu-id="1b4ed-111">Para criar um `ManifestResource` estrutura de metadados, use o [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1b4ed-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b4ed-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b4ed-112">Requirements</span></span>  
 <span data-ttu-id="1b4ed-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b4ed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b4ed-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b4ed-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b4ed-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1b4ed-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b4ed-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b4ed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b4ed-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b4ed-117">See Also</span></span>  
 [<span data-ttu-id="1b4ed-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="1b4ed-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

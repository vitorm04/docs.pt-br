---
title: Método IMetaDataAssemblyEmit::SetManifestResourceProps
ms.date: 03/30/2017
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
ms.openlocfilehash: 9370b27fd385b0223b354365d64aa57048f4ec69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177839"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="ff182-102">Método IMetaDataAssemblyEmit::SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="ff182-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="ff182-103">Modifica a estrutura `ManifestResource` de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="ff182-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff182-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff182-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff182-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff182-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="ff182-106">[em] O token que `ManifestResource` especifica a estrutura de metadados a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="ff182-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="ff182-107">[em] O token, `File` de `AssemblyRef`tipo ou , que mapeia para o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="ff182-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="ff182-108">[em] A compensação para o início do recurso dentro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ff182-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="ff182-109">[em] Uma combinação bitwise de valores de bandeira que especificam os atributos do recurso.</span><span class="sxs-lookup"><span data-stu-id="ff182-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff182-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff182-110">Remarks</span></span>  
 <span data-ttu-id="ff182-111">Para criar `ManifestResource` uma estrutura de metadados, use o método [IMetaDataAssemblyEmit::DefineManifestResource.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)</span><span class="sxs-lookup"><span data-stu-id="ff182-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff182-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff182-112">Requirements</span></span>  
 <span data-ttu-id="ff182-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff182-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff182-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff182-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff182-115">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff182-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff182-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff182-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff182-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="ff182-117">See also</span></span>

- [<span data-ttu-id="ff182-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="ff182-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

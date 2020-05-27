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
ms.openlocfilehash: 74111a175b0decbc1beef7c8df5ade59d31d845b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009139"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="15244-102">Método IMetaDataAssemblyEmit::SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="15244-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="15244-103">Modifica a estrutura de `ManifestResource` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="15244-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15244-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15244-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15244-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15244-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="15244-106">no O token que especifica a `ManifestResource` estrutura de metadados a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="15244-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="15244-107">no O token, do tipo `File` ou `AssemblyRef` , que é mapeado para o provedor de recursos.</span><span class="sxs-lookup"><span data-stu-id="15244-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="15244-108">no O deslocamento para o início do recurso dentro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="15244-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="15244-109">no Uma combinação de bits de valor de sinalizador que especifica os atributos do recurso.</span><span class="sxs-lookup"><span data-stu-id="15244-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15244-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="15244-110">Remarks</span></span>  
 <span data-ttu-id="15244-111">Para criar uma `ManifestResource` estrutura de metadados, use o método [IMetaDataAssemblyEmit::D efinemanifestresource](imetadataassemblyemit-definemanifestresource-method.md) .</span><span class="sxs-lookup"><span data-stu-id="15244-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15244-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15244-112">Requirements</span></span>  
 <span data-ttu-id="15244-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15244-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15244-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="15244-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15244-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15244-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15244-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15244-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15244-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="15244-117">See also</span></span>

- [<span data-ttu-id="15244-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="15244-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

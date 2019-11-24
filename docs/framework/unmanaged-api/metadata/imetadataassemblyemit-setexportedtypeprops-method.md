---
title: Método IMetaDataAssemblyEmit::SetExportedTypeProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: ae682c354a7a5188611b103008a3e18f8d821260
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431934"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="83d27-102">Método IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="83d27-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="83d27-103">Modifies the specified `ExportedType` metadata structure.</span><span class="sxs-lookup"><span data-stu-id="83d27-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d27-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83d27-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83d27-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83d27-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="83d27-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span><span class="sxs-lookup"><span data-stu-id="83d27-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="83d27-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span><span class="sxs-lookup"><span data-stu-id="83d27-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="83d27-108">[in] The `TypeDef` token referenced in the code file.</span><span class="sxs-lookup"><span data-stu-id="83d27-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="83d27-109">[in] A bitwise combination of values that specify attributes of the type.</span><span class="sxs-lookup"><span data-stu-id="83d27-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83d27-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="83d27-110">Remarks</span></span>  
 <span data-ttu-id="83d27-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="83d27-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83d27-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83d27-112">Requirements</span></span>  
 <span data-ttu-id="83d27-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d27-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d27-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83d27-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83d27-115">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83d27-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83d27-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83d27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d27-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83d27-117">See also</span></span>

- [<span data-ttu-id="83d27-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="83d27-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

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
ms.openlocfilehash: dd1d6f1da6e49837eebd9356500f403c199b011b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177847"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="f356e-102">Método IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="f356e-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="f356e-103">Modifica a estrutura `ExportedType` de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="f356e-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f356e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f356e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f356e-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f356e-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="f356e-106">[em] O token de metadados `ExportedType` que especifica a estrutura de metadados a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="f356e-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="f356e-107">[em] O token, `File`do `AssemblyRef`tipo, ou `ExportedType`, que especifica como este tipo é implementado.</span><span class="sxs-lookup"><span data-stu-id="f356e-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="f356e-108">[em] O `TypeDef` token referenciado no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="f356e-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="f356e-109">[em] Uma combinação bitwise de valores que especificam atributos do tipo.</span><span class="sxs-lookup"><span data-stu-id="f356e-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f356e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f356e-110">Remarks</span></span>  
 <span data-ttu-id="f356e-111">Para criar `ExportedType` uma estrutura de metadados, use o método [IMetaDataAssemblyEmit::DefineExportedType.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)</span><span class="sxs-lookup"><span data-stu-id="f356e-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f356e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f356e-112">Requirements</span></span>  
 <span data-ttu-id="f356e-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f356e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f356e-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f356e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f356e-115">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f356e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f356e-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f356e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f356e-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="f356e-117">See also</span></span>

- [<span data-ttu-id="f356e-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="f356e-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8643a4d207fb570195caa00a1ac659c78c2ff2b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="997ee-102">Método IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="997ee-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="997ee-103">Modifica especificado `ExportedType` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="997ee-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="997ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="997ee-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="997ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="997ee-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="997ee-106">[in] O token de metadados que especifica o `ExportedType` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="997ee-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="997ee-107">[in] O token, do tipo `File`, `AssemblyRef`, ou `ExportedType`, que especifica como este tipo é implementado.</span><span class="sxs-lookup"><span data-stu-id="997ee-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="997ee-108">[in] O `TypeDef` referenciado no arquivo de código de token.</span><span class="sxs-lookup"><span data-stu-id="997ee-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="997ee-109">[in] Uma combinação bit a bit de valores que especificam os atributos do tipo.</span><span class="sxs-lookup"><span data-stu-id="997ee-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="997ee-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="997ee-110">Remarks</span></span>  
 <span data-ttu-id="997ee-111">Para criar um `ExportedType` estrutura de metadados, use o [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="997ee-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="997ee-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="997ee-112">Requirements</span></span>  
 <span data-ttu-id="997ee-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="997ee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="997ee-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="997ee-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="997ee-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="997ee-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="997ee-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="997ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="997ee-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="997ee-117">See Also</span></span>  
 [<span data-ttu-id="997ee-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="997ee-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

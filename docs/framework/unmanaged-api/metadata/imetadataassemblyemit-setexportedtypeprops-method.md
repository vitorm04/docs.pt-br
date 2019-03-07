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
ms.openlocfilehash: e5fff28e1c2c0d31285c9621c184a44355813a03
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479682"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="e087f-102">Método IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="e087f-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="e087f-103">Modifica especificado `ExportedType` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="e087f-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e087f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e087f-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e087f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e087f-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="e087f-106">[in] O token de metadados que especifica o `ExportedType` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="e087f-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="e087f-107">[in] O token, do tipo `File`, `AssemblyRef`, ou `ExportedType`, que especifica como esse tipo é implementado.</span><span class="sxs-lookup"><span data-stu-id="e087f-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="e087f-108">[in] O `TypeDef` token referenciado no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="e087f-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="e087f-109">[in] Uma combinação bit a bit dos valores que especificam os atributos do tipo.</span><span class="sxs-lookup"><span data-stu-id="e087f-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e087f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e087f-110">Remarks</span></span>  
 <span data-ttu-id="e087f-111">Para criar uma `ExportedType` estrutura de metadados, use o [imetadataassemblyemit:: Defineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e087f-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e087f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e087f-112">Requirements</span></span>  
 <span data-ttu-id="e087f-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e087f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e087f-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e087f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e087f-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e087f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e087f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e087f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e087f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e087f-117">See also</span></span>
- [<span data-ttu-id="e087f-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="e087f-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

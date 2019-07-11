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
ms.openlocfilehash: e4be840760782789aa91e5519f60374aca2e3941
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775258"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="6d1dc-102">Método IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="6d1dc-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="6d1dc-103">Modifica especificado `ExportedType` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="6d1dc-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d1dc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d1dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d1dc-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="6d1dc-106">[in] O token de metadados que especifica o `ExportedType` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="6d1dc-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="6d1dc-107">[in] O token, do tipo `File`, `AssemblyRef`, ou `ExportedType`, que especifica como esse tipo é implementado.</span><span class="sxs-lookup"><span data-stu-id="6d1dc-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="6d1dc-108">[in] O `TypeDef` token referenciado no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="6d1dc-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="6d1dc-109">[in] Uma combinação bit a bit dos valores que especificam os atributos do tipo.</span><span class="sxs-lookup"><span data-stu-id="6d1dc-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d1dc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d1dc-110">Remarks</span></span>  
 <span data-ttu-id="6d1dc-111">Para criar uma `ExportedType` estrutura de metadados, use o [imetadataassemblyemit:: Defineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="6d1dc-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d1dc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d1dc-112">Requirements</span></span>  
 <span data-ttu-id="6d1dc-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d1dc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d1dc-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d1dc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d1dc-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6d1dc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d1dc-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d1dc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1dc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d1dc-117">See also</span></span>

- [<span data-ttu-id="6d1dc-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="6d1dc-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

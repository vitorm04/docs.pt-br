---
title: "Método IMetaDataAssemblyEmit::SetExportedTypeProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c41cc2c6433139f1e1f355585e4af0a8f01c7c94
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="bbe6b-102">Método IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="bbe6b-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="bbe6b-103">Modifica especificado `ExportedType` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbe6b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbe6b-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbe6b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbe6b-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="bbe6b-106">[in] O token de metadados que especifica o `ExportedType` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="bbe6b-107">[in] O token, do tipo `File`, `AssemblyRef`, ou `ExportedType`, que especifica como este tipo é implementado.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="bbe6b-108">[in] O `TypeDef` referenciado no arquivo de código de token.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="bbe6b-109">[in] Uma combinação bit a bit de valores que especificam os atributos do tipo.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbe6b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbe6b-110">Remarks</span></span>  
 <span data-ttu-id="bbe6b-111">Para criar um `ExportedType` estrutura de metadados, use o [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbe6b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbe6b-112">Requirements</span></span>  
 <span data-ttu-id="bbe6b-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbe6b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbe6b-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bbe6b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bbe6b-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bbe6b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bbe6b-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbe6b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe6b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbe6b-117">See Also</span></span>  
 [<span data-ttu-id="bbe6b-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="bbe6b-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

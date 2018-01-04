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
ms.workload: dotnet
ms.openlocfilehash: bebcf827488912431cb0f94f5527d3445fc41125
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="9f604-102">Método IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="9f604-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="9f604-103">Modifica especificado `ExportedType` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="9f604-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f604-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f604-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f604-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f604-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="9f604-106">[in] O token de metadados que especifica o `ExportedType` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="9f604-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="9f604-107">[in] O token, do tipo `File`, `AssemblyRef`, ou `ExportedType`, que especifica como este tipo é implementado.</span><span class="sxs-lookup"><span data-stu-id="9f604-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="9f604-108">[in] O `TypeDef` referenciado no arquivo de código de token.</span><span class="sxs-lookup"><span data-stu-id="9f604-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="9f604-109">[in] Uma combinação bit a bit de valores que especificam os atributos do tipo.</span><span class="sxs-lookup"><span data-stu-id="9f604-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f604-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f604-110">Remarks</span></span>  
 <span data-ttu-id="9f604-111">Para criar um `ExportedType` estrutura de metadados, use o [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="9f604-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f604-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f604-112">Requirements</span></span>  
 <span data-ttu-id="9f604-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f604-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f604-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9f604-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f604-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9f604-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f604-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f604-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f604-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f604-117">See Also</span></span>  
 [<span data-ttu-id="9f604-118">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="9f604-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

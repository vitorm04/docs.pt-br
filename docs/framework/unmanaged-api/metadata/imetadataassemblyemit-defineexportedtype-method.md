---
title: "Método IMetaDataAssemblyEmit::DefineExportedType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineExportedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 245a485289335b096ee60a8eb3696a087e6871e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="5e799-102">Método IMetaDataAssemblyEmit::DefineExportedType</span><span class="sxs-lookup"><span data-stu-id="5e799-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="5e799-103">Cria um `ExportedType` estrutura que contém os metadados de tipo exportado de especificado e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="5e799-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e799-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e799-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e799-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5e799-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="5e799-106">[in] O nome do tipo a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="5e799-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="5e799-107">Para a versão 1.1 do common language runtime, o nome do tipo exportado deve corresponder exatamente ao nome fornecido no `TypeDef` para o tipo.</span><span class="sxs-lookup"><span data-stu-id="5e799-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="5e799-108">[in] Um token especificando onde o tipo exportado é implementado.</span><span class="sxs-lookup"><span data-stu-id="5e799-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="5e799-109">Os valores válidos e seus significados associados são:</span><span class="sxs-lookup"><span data-stu-id="5e799-109">The valid values and their associated meanings are:</span></span>  
  
-   <span data-ttu-id="5e799-110">`mdFile`O tipo é implementado em um arquivo diferente dentro desse assembly.</span><span class="sxs-lookup"><span data-stu-id="5e799-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
-   <span data-ttu-id="5e799-111">`mdAssemblyRef`O tipo é implementado em um assembly diferente.</span><span class="sxs-lookup"><span data-stu-id="5e799-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
-   <span data-ttu-id="5e799-112">`mdExportedTYpe`O tipo é aninhado dentro de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="5e799-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
-   <span data-ttu-id="5e799-113">`mdFileNil`O tipo está no mesmo arquivo de manifesto e não é um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="5e799-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="5e799-114">[in] Um token de metadados que especifica o tipo a ser exportado.</span><span class="sxs-lookup"><span data-stu-id="5e799-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="5e799-115">Esse valor é inserido no `TypeDef` tabela no arquivo que implementa o tipo e é relevante somente se esse arquivo está nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="5e799-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="5e799-116">[in] Uma combinação bit a bit de [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) valores de enumeração que define as configurações de propriedade para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="5e799-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="5e799-117">[out] Um ponteiro para o token de metadados retornados que indica o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="5e799-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e799-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e799-118">Remarks</span></span>  
 <span data-ttu-id="5e799-119">Um `ExportedType` estrutura de metadados deve ser definida para cada tipo que é exposto por este assembly e é implementado em um módulo diferente daquele que contém o manifesto.</span><span class="sxs-lookup"><span data-stu-id="5e799-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e799-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e799-120">Requirements</span></span>  
 <span data-ttu-id="5e799-121">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e799-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e799-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5e799-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e799-123">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5e799-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e799-124">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e799-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e799-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e799-125">See Also</span></span>  
 [<span data-ttu-id="5e799-126">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="5e799-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

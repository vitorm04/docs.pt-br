---
title: Método IMetaDataAssemblyImport::GetExportedTypeProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8dd1daf3528bbc642033e254a809c18c3662ff1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779187"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="6a390-102">Método IMetaDataAssemblyImport::GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="6a390-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="6a390-103">Obtém o conjunto de propriedades do tipo exportado com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="6a390-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a390-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a390-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a390-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a390-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="6a390-106">[in] Um `mdExportedType` token de metadados que representa o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="6a390-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="6a390-107">[out] O nome do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="6a390-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6a390-108">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="6a390-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="6a390-109">[out] O número de caracteres largos, na verdade, retornadas no `szName`</span><span class="sxs-lookup"><span data-stu-id="6a390-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="6a390-110">[out] Uma `mdFile`, `mdAssemblyRef`, ou `mdExportedType` token de metadados que contém ou permite o acesso às propriedades do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="6a390-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="6a390-111">[out] Um ponteiro para um `mdTypeDef` token que representa um tipo no arquivo.</span><span class="sxs-lookup"><span data-stu-id="6a390-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="6a390-112">[out] Um ponteiro para os sinalizadores que descrevem os metadados aplicados ao tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="6a390-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="6a390-113">O valor de sinalizadores pode ser um ou mais [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="6a390-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a390-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a390-114">Requirements</span></span>  
 <span data-ttu-id="6a390-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a390-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a390-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a390-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a390-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6a390-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a390-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a390-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a390-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a390-119">See also</span></span>

- [<span data-ttu-id="6a390-120">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="6a390-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

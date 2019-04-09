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
ms.openlocfilehash: 91b1e4469f07954dc433769911c78d72bb3c36cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096144"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="c0fa7-102">Método IMetaDataAssemblyImport::GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="c0fa7-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="c0fa7-103">Obtém o conjunto de propriedades do tipo exportado com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="c0fa7-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0fa7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0fa7-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="c0fa7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0fa7-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="c0fa7-106">[in] Um `mdExportedType` token de metadados que representa o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="c0fa7-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="c0fa7-107">[out] O nome do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="c0fa7-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c0fa7-108">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="c0fa7-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c0fa7-109">[out] O número de caracteres largos, na verdade, retornadas no</span><span class="sxs-lookup"><span data-stu-id="c0fa7-109">[out] The number of wide characters actually returned in</span></span> `szName`  
  
 `ptkImplementation`  
 <span data-ttu-id="c0fa7-110">[out] Uma `mdFile`, `mdAssemblyRef`, ou `mdExportedType` token de metadados que contém ou permite o acesso às propriedades do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="c0fa7-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="c0fa7-111">[out] Um ponteiro para um `mdTypeDef` token que representa um tipo no arquivo.</span><span class="sxs-lookup"><span data-stu-id="c0fa7-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="c0fa7-112">[out] Um ponteiro para os sinalizadores que descrevem os metadados aplicados ao tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="c0fa7-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="c0fa7-113">O valor de sinalizadores pode ser um ou mais [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="c0fa7-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0fa7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0fa7-114">Requirements</span></span>  
 <span data-ttu-id="c0fa7-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0fa7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0fa7-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0fa7-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0fa7-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c0fa7-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c0fa7-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c0fa7-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0fa7-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0fa7-119">See also</span></span>

- [<span data-ttu-id="c0fa7-120">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="c0fa7-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

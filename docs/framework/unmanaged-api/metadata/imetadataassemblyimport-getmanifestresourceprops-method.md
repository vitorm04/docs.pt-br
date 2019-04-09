---
title: Método IMetaDataAssemblyImport::GetManifestResourceProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba99d84686974b425bcdee0bbf4770e4843e1351
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081652"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="08615-102">Método IMetaDataAssemblyImport::GetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="08615-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="08615-103">Obtém o conjunto de propriedades do recurso de manifesto com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="08615-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08615-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08615-104">Syntax</span></span>  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08615-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08615-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="08615-106">[in] Um `mdManifestResource` token que representa o recurso para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="08615-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="08615-107">[out] O nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="08615-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="08615-108">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="08615-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="08615-109">[out] Um ponteiro para o número de caracteres largos, na verdade, é retornado no `szName`.</span><span class="sxs-lookup"><span data-stu-id="08615-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="08615-110">[out] Um ponteiro para um `mdFile` token ou um `mdAssemblyRef` token que representa o arquivo ou assembly, respectivamente, que contém o recurso.</span><span class="sxs-lookup"><span data-stu-id="08615-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="08615-111">[out] Um ponteiro para um valor que especifica o deslocamento para o início do recurso dentro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="08615-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="08615-112">[out] Um ponteiro para os sinalizadores que descrevem os metadados aplicado a um recurso.</span><span class="sxs-lookup"><span data-stu-id="08615-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="08615-113">O valor de sinalizadores é uma combinação de um ou mais [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="08615-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08615-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08615-114">Requirements</span></span>  
 <span data-ttu-id="08615-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08615-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08615-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08615-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08615-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="08615-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="08615-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="08615-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="08615-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08615-119">See also</span></span>

- [<span data-ttu-id="08615-120">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="08615-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

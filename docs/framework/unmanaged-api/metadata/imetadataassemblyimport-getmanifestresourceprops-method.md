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
ms.openlocfilehash: c1792ed0f15f8cfb62567593c9694453650f0bb9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436320"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="47803-102">Método IMetaDataAssemblyImport::GetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="47803-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="47803-103">Obtém o conjunto de propriedades do recurso de manifesto com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="47803-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47803-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47803-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="47803-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47803-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="47803-106">no Um `mdManifestResource` token que representa o recurso para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="47803-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="47803-107">fora O nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="47803-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="47803-108">no O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="47803-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="47803-109">fora Um ponteiro para o número de caracteres largos realmente retornados em `szName`.</span><span class="sxs-lookup"><span data-stu-id="47803-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="47803-110">fora Um ponteiro para um token de `mdFile` ou um token de `mdAssemblyRef` que representa o arquivo ou assembly, respectivamente, que contém o recurso.</span><span class="sxs-lookup"><span data-stu-id="47803-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="47803-111">fora Um ponteiro para um valor que especifica o deslocamento para o início do recurso dentro do arquivo.</span><span class="sxs-lookup"><span data-stu-id="47803-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="47803-112">fora Um ponteiro para sinalizadores que descrevem os metadados aplicados a um recurso.</span><span class="sxs-lookup"><span data-stu-id="47803-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="47803-113">O valor de flags é uma combinação de um ou mais valores de [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="47803-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47803-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="47803-114">Requirements</span></span>  
 <span data-ttu-id="47803-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47803-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47803-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="47803-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47803-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="47803-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47803-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47803-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47803-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47803-119">See also</span></span>

- [<span data-ttu-id="47803-120">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="47803-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

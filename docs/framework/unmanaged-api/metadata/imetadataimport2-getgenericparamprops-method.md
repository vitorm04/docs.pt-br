---
title: Método IMetaDataImport2::GetGenericParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf9f6cc1e568463f2ca9afa38c10f50d0c247013
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755346"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="e4c38-102">Método IMetaDataImport2::GetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="e4c38-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="e4c38-103">Obtém os metadados associados com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="e4c38-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4c38-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4c38-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4c38-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="e4c38-106">[in] O token que representa o parâmetro genérico para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="e4c38-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="e4c38-107">[out] A posição ordinal do `Type` parâmetro no método ou Construtor de pai.</span><span class="sxs-lookup"><span data-stu-id="e4c38-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="e4c38-108">[out] Um valor igual a [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeração que descreve o `Type` para o parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="e4c38-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="e4c38-109">[out] Um token de TypeDef ou MethodDef que representa o proprietário do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e4c38-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="e4c38-110">[out] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="e4c38-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="e4c38-111">[out] O nome do parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="e4c38-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e4c38-112">[in] O tamanho do `wzName` buffer.</span><span class="sxs-lookup"><span data-stu-id="e4c38-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="e4c38-113">[out] O tamanho retornado do nome, em caracteres largos.</span><span class="sxs-lookup"><span data-stu-id="e4c38-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4c38-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4c38-114">Requirements</span></span>  
 <span data-ttu-id="e4c38-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4c38-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4c38-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e4c38-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4c38-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e4c38-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4c38-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4c38-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c38-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4c38-119">See also</span></span>

- [<span data-ttu-id="e4c38-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e4c38-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="e4c38-121">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e4c38-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

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
ms.openlocfilehash: 15b58e01d4ce99f19f510c760819471b84380b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177766"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="e616e-102">Método IMetaDataAssemblyImport::GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="e616e-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="e616e-103">Obtém o conjunto de propriedades do tipo exportado com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="e616e-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e616e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e616e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e616e-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e616e-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="e616e-106">[em] Um `mdExportedType` token de metadados que representa o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="e616e-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="e616e-107">[fora] O nome do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="e616e-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e616e-108">[em] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="e616e-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="e616e-109">[fora] O número de personagens largos realmente retornou em`szName`</span><span class="sxs-lookup"><span data-stu-id="e616e-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="e616e-110">[fora] Um `mdFile` `mdAssemblyRef`, `mdExportedType` ou token de metadados que contenha ou permita acesso às propriedades do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="e616e-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="e616e-111">[fora] Um ponteiro `mdTypeDef` para um token que representa um tipo no arquivo.</span><span class="sxs-lookup"><span data-stu-id="e616e-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="e616e-112">[fora] Um ponteiro para as bandeiras que descrevem os metadados aplicados ao tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="e616e-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="e616e-113">O valor das bandeiras pode ser um ou mais valores [de CorTypeAttr.](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="e616e-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e616e-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e616e-114">Requirements</span></span>  
 <span data-ttu-id="e616e-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e616e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e616e-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e616e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e616e-117">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e616e-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e616e-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e616e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e616e-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="e616e-119">See also</span></span>

- [<span data-ttu-id="e616e-120">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="e616e-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

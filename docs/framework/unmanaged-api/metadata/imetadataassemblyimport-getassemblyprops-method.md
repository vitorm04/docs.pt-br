---
title: Método IMetaDataAssemblyImport::GetAssemblyProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74295b14e9c774aa8a61d9c2726a39a4e3f5f8cc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477706"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="8ec9d-102">Método IMetaDataAssemblyImport::GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="8ec9d-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="8ec9d-103">Obtém o conjunto de propriedades para o assembly com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec9d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ec9d-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ec9d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ec9d-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="8ec9d-106">[in].</span><span class="sxs-lookup"><span data-stu-id="8ec9d-106">[in].</span></span> <span data-ttu-id="8ec9d-107">O `mdAssembly` token de metadados que representa o assembly para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="8ec9d-108">[out] Um ponteiro para a chave pública ou token de metadados.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="8ec9d-109">[out] O número de bytes na chave pública retornada.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="8ec9d-110">[out] Um ponteiro para o algoritmo usado para os arquivos no assembly de hash.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="8ec9d-111">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8ec9d-112">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8ec9d-113">[out] O número de caracteres largos, na verdade, é retornado no `szName`.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="8ec9d-114">[out] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="8ec9d-115">[out] Sinalizadores que descrevem os metadados aplicados a um assembly.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="8ec9d-116">Esse valor é uma combinação de um ou mais [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="8ec9d-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ec9d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ec9d-117">Requirements</span></span>  
 <span data-ttu-id="8ec9d-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ec9d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ec9d-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ec9d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ec9d-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8ec9d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ec9d-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ec9d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec9d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ec9d-122">See also</span></span>
- [<span data-ttu-id="8ec9d-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="8ec9d-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

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
ms.openlocfilehash: 911d0d1444e2cf3cb8241eeeff63a5a86b4ab806
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446268"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="2031e-102">Método IMetaDataAssemblyImport::GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="2031e-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="2031e-103">Obtém o conjunto de propriedades para o assembly com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="2031e-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2031e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2031e-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="2031e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2031e-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="2031e-106">[in].</span><span class="sxs-lookup"><span data-stu-id="2031e-106">[in].</span></span> <span data-ttu-id="2031e-107">O `mdAssembly` token de metadados que representa o assembly para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="2031e-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="2031e-108">[out] Um ponteiro para a chave pública ou token de metadados.</span><span class="sxs-lookup"><span data-stu-id="2031e-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="2031e-109">[out] O número de bytes a chave pública retornado.</span><span class="sxs-lookup"><span data-stu-id="2031e-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="2031e-110">[out] Um ponteiro para o algoritmo usado para os arquivos no assembly de hash.</span><span class="sxs-lookup"><span data-stu-id="2031e-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="2031e-111">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="2031e-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2031e-112">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="2031e-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2031e-113">[out] O número de caracteres largos realmente retornados em `szName`.</span><span class="sxs-lookup"><span data-stu-id="2031e-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="2031e-114">[out] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="2031e-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="2031e-115">[out] Sinalizadores que descrevem os metadados aplicado a um assembly.</span><span class="sxs-lookup"><span data-stu-id="2031e-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="2031e-116">Esse valor é uma combinação de um ou mais [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="2031e-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2031e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2031e-117">Requirements</span></span>  
 <span data-ttu-id="2031e-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2031e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2031e-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2031e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2031e-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2031e-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2031e-121">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2031e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2031e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2031e-122">See Also</span></span>  
 [<span data-ttu-id="2031e-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="2031e-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

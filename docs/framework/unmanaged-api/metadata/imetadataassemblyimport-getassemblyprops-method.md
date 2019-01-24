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
ms.openlocfilehash: bcf1dca8799ac082c025e602e5d82c99d42650d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659599"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="bd43c-102">Método IMetaDataAssemblyImport::GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="bd43c-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="bd43c-103">Obtém o conjunto de propriedades para o assembly com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="bd43c-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd43c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd43c-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="bd43c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd43c-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="bd43c-106">[in].</span><span class="sxs-lookup"><span data-stu-id="bd43c-106">[in].</span></span> <span data-ttu-id="bd43c-107">O `mdAssembly` token de metadados que representa o assembly para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="bd43c-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="bd43c-108">[out] Um ponteiro para a chave pública ou token de metadados.</span><span class="sxs-lookup"><span data-stu-id="bd43c-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="bd43c-109">[out] O número de bytes na chave pública retornada.</span><span class="sxs-lookup"><span data-stu-id="bd43c-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="bd43c-110">[out] Um ponteiro para o algoritmo usado para os arquivos no assembly de hash.</span><span class="sxs-lookup"><span data-stu-id="bd43c-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="bd43c-111">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="bd43c-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bd43c-112">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="bd43c-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="bd43c-113">[out] O número de caracteres largos, na verdade, é retornado no `szName`.</span><span class="sxs-lookup"><span data-stu-id="bd43c-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="bd43c-114">[out] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="bd43c-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="bd43c-115">[out] Sinalizadores que descrevem os metadados aplicados a um assembly.</span><span class="sxs-lookup"><span data-stu-id="bd43c-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="bd43c-116">Esse valor é uma combinação de um ou mais [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="bd43c-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd43c-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd43c-117">Requirements</span></span>  
 <span data-ttu-id="bd43c-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd43c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd43c-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd43c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd43c-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bd43c-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd43c-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd43c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd43c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd43c-122">See also</span></span>
- [<span data-ttu-id="bd43c-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="bd43c-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

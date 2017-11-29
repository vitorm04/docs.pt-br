---
title: "Método IMetaDataAssemblyImport::GetAssemblyProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3ff9c66d483392823a1cc95163e4d5e7e81a364
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="5fb42-102">Método IMetaDataAssemblyImport::GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="5fb42-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="5fb42-103">Obtém o conjunto de propriedades para o assembly com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="5fb42-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb42-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fb42-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="5fb42-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5fb42-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="5fb42-106">[in].</span><span class="sxs-lookup"><span data-stu-id="5fb42-106">[in].</span></span> <span data-ttu-id="5fb42-107">O `mdAssembly` token de metadados que representa o assembly para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="5fb42-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="5fb42-108">[out] Um ponteiro para a chave pública ou token de metadados.</span><span class="sxs-lookup"><span data-stu-id="5fb42-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="5fb42-109">[out] O número de bytes a chave pública retornado.</span><span class="sxs-lookup"><span data-stu-id="5fb42-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="5fb42-110">[out] Um ponteiro para o algoritmo usado para os arquivos no assembly de hash.</span><span class="sxs-lookup"><span data-stu-id="5fb42-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="5fb42-111">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="5fb42-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5fb42-112">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="5fb42-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5fb42-113">[out] O número de caracteres largos realmente retornados em `szName`.</span><span class="sxs-lookup"><span data-stu-id="5fb42-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5fb42-114">[out] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="5fb42-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="5fb42-115">[out] Sinalizadores que descrevem os metadados aplicado a um assembly.</span><span class="sxs-lookup"><span data-stu-id="5fb42-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="5fb42-116">Esse valor é uma combinação de um ou mais [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="5fb42-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fb42-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5fb42-117">Requirements</span></span>  
 <span data-ttu-id="5fb42-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fb42-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fb42-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5fb42-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fb42-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5fb42-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5fb42-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fb42-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb42-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fb42-122">See Also</span></span>  
 [<span data-ttu-id="5fb42-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="5fb42-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

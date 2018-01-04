---
title: "Método IMetaDataAssemblyImport::GetFileProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetFileProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55984c4adaf291e3b962514cdc3bea964d1c91bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="fc0f1-102">Método IMetaDataAssemblyImport::GetFileProps</span><span class="sxs-lookup"><span data-stu-id="fc0f1-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="fc0f1-103">Obtém as propriedades do arquivo com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0f1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc0f1-104">Syntax</span></span>  
  
```  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc0f1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc0f1-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="fc0f1-106">[in] O `mdFile` token de metadados que representa o arquivo para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="fc0f1-107">[out] O nome simples do arquivo.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="fc0f1-108">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="fc0f1-109">[out] O número de caracteres largos realmente retornados em `szName`.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="fc0f1-110">[out] Um ponteiro para o valor de hash.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="fc0f1-111">Este é o hash, usando o algoritmo SHA-1, do arquivo.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="fc0f1-112">[out] O número de caracteres largos no valor de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="fc0f1-113">[out] Um ponteiro para os sinalizadores que descrevem os metadados aplicado a um arquivo.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="fc0f1-114">O valor de sinalizadores é uma combinação de um ou mais [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="fc0f1-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc0f1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc0f1-115">Requirements</span></span>  
 <span data-ttu-id="fc0f1-116">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc0f1-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc0f1-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc0f1-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc0f1-118">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fc0f1-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc0f1-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc0f1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0f1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc0f1-120">See Also</span></span>  
 [<span data-ttu-id="fc0f1-121">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="fc0f1-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

---
title: Método IMetaDataAssemblyImport::GetFileProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da38c04f5d67dc0220b1828ba0e5cdeb84346bb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044454"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="6d4a9-102">Método IMetaDataAssemblyImport::GetFileProps</span><span class="sxs-lookup"><span data-stu-id="6d4a9-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="6d4a9-103">Obtém as propriedades do arquivo com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d4a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d4a9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6d4a9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d4a9-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="6d4a9-106">[in] O `mdFile` token de metadados que representa o arquivo para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="6d4a9-107">[out] O nome simples do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6d4a9-108">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="6d4a9-109">[out] O número de caracteres largos, na verdade, é retornado no `szName`.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="6d4a9-110">[out] Um ponteiro para o valor de hash.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="6d4a9-111">Isso é o hash, usando o algoritmo SHA-1, do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="6d4a9-112">[out] O número de caracteres largos no valor de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="6d4a9-113">[out] Um ponteiro para os sinalizadores que descrevem os metadados aplicado a um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="6d4a9-114">O valor de sinalizadores é uma combinação de um ou mais [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="6d4a9-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d4a9-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d4a9-115">Requirements</span></span>  
 <span data-ttu-id="6d4a9-116">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d4a9-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d4a9-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d4a9-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d4a9-118">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6d4a9-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d4a9-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d4a9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4a9-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d4a9-120">See also</span></span>

- [<span data-ttu-id="6d4a9-121">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="6d4a9-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

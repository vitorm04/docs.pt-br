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
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175974"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="bbd2b-102">Método IMetaDataAssemblyImport::GetFileProps</span><span class="sxs-lookup"><span data-stu-id="bbd2b-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="bbd2b-103">Obtém as propriedades do arquivo com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="bbd2b-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd2b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbd2b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="bbd2b-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbd2b-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="bbd2b-106">[em] O `mdFile` token de metadados que representa o arquivo para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="bbd2b-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="bbd2b-107">[fora] O nome simples do arquivo.</span><span class="sxs-lookup"><span data-stu-id="bbd2b-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bbd2b-108">[em] O tamanho, em grandes `szName`chars, de .</span><span class="sxs-lookup"><span data-stu-id="bbd2b-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="bbd2b-109">[fora] O número de chars largos realmente retornou em `szName`.</span><span class="sxs-lookup"><span data-stu-id="bbd2b-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="bbd2b-110">[fora] Um ponteiro para o valor de hash.</span><span class="sxs-lookup"><span data-stu-id="bbd2b-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="bbd2b-111">Este é o hash, usando o algoritmo SHA-1, do arquivo.</span><span class="sxs-lookup"><span data-stu-id="bbd2b-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="bbd2b-112">[fora] O número de chars largos no valor de hash devolvido.</span><span class="sxs-lookup"><span data-stu-id="bbd2b-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="bbd2b-113">[fora] Um ponteiro para as bandeiras que descrevem os metadados aplicados a um arquivo.</span><span class="sxs-lookup"><span data-stu-id="bbd2b-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="bbd2b-114">O valor dos sinalizadores é uma combinação de um ou mais valores [corfileflags.](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="bbd2b-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbd2b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbd2b-115">Requirements</span></span>  
 <span data-ttu-id="bbd2b-116">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbd2b-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbd2b-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bbd2b-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bbd2b-118">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bbd2b-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bbd2b-119">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbd2b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd2b-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="bbd2b-120">See also</span></span>

- [<span data-ttu-id="bbd2b-121">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="bbd2b-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

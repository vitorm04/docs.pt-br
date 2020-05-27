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
ms.openlocfilehash: 78c192f10f629a0c1316ae7af7fc774819f4de8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007475"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="66f13-102">Método IMetaDataAssemblyImport::GetFileProps</span><span class="sxs-lookup"><span data-stu-id="66f13-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="66f13-103">Obtém as propriedades do arquivo com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="66f13-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66f13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66f13-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="66f13-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66f13-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="66f13-106">no O `mdFile` token de metadados que representa o arquivo para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="66f13-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="66f13-107">fora O nome simples do arquivo.</span><span class="sxs-lookup"><span data-stu-id="66f13-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="66f13-108">no O tamanho, em caracteres largos, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="66f13-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="66f13-109">fora O número de caracteres largos realmente retornados em `szName` .</span><span class="sxs-lookup"><span data-stu-id="66f13-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="66f13-110">fora Um ponteiro para o valor de hash.</span><span class="sxs-lookup"><span data-stu-id="66f13-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="66f13-111">Esse é o hash, usando o algoritmo SHA-1 do arquivo.</span><span class="sxs-lookup"><span data-stu-id="66f13-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="66f13-112">fora O número de caracteres largos no valor de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="66f13-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="66f13-113">fora Um ponteiro para os sinalizadores que descrevem os metadados aplicados a um arquivo.</span><span class="sxs-lookup"><span data-stu-id="66f13-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="66f13-114">O valor de flags é uma combinação de um ou mais valores de [CorFileFlags](corfileflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="66f13-114">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66f13-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66f13-115">Requirements</span></span>  
 <span data-ttu-id="66f13-116">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66f13-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66f13-117">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="66f13-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66f13-118">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="66f13-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66f13-119">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66f13-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f13-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="66f13-120">See also</span></span>

- [<span data-ttu-id="66f13-121">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="66f13-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)

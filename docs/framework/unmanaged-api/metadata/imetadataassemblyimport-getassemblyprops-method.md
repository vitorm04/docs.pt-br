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
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177782"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="36045-102">Método IMetaDataAssemblyImport::GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="36045-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="36045-103">Obtém o conjunto de propriedades para o conjunto com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="36045-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36045-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36045-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="36045-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="36045-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="36045-106">[in].</span><span class="sxs-lookup"><span data-stu-id="36045-106">[in].</span></span> <span data-ttu-id="36045-107">O `mdAssembly` token de metadados que representa o conjunto para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="36045-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="36045-108">[fora] Um ponteiro para a chave pública ou o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="36045-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="36045-109">[fora] O número de bytes na chave pública devolvida.</span><span class="sxs-lookup"><span data-stu-id="36045-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="36045-110">[fora] Um ponteiro para o algoritmo usado para hash os arquivos na montagem.</span><span class="sxs-lookup"><span data-stu-id="36045-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="36045-111">[fora] O nome simples da assembléia.</span><span class="sxs-lookup"><span data-stu-id="36045-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="36045-112">[em] O tamanho, em grandes `szName`chars, de .</span><span class="sxs-lookup"><span data-stu-id="36045-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="36045-113">[fora] O número de chars largos realmente retornou em `szName`.</span><span class="sxs-lookup"><span data-stu-id="36045-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="36045-114">[fora] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do conjunto.</span><span class="sxs-lookup"><span data-stu-id="36045-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="36045-115">[fora] Sinalizadores que descrevem os metadados aplicados a uma montagem.</span><span class="sxs-lookup"><span data-stu-id="36045-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="36045-116">Este valor é uma combinação de um ou mais valores [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="36045-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36045-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36045-117">Requirements</span></span>  
 <span data-ttu-id="36045-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36045-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36045-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="36045-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36045-120">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36045-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36045-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36045-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36045-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="36045-122">See also</span></span>

- [<span data-ttu-id="36045-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="36045-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

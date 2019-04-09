---
title: Método IMetaDataAssemblyImport::GetAssemblyRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6c550ff7af2dda8bc06afd771024fe290339904
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089777"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="fbfec-102">Método IMetaDataAssemblyImport::GetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="fbfec-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="fbfec-103">Obtém o conjunto de propriedades para a referência de assembly com a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="fbfec-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbfec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbfec-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbfec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbfec-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="fbfec-106">[in] O `mdAssemblyRef` token de metadados que representa a referência de assembly para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="fbfec-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="fbfec-107">[out] Um ponteiro para a chave pública ou token de metadados.</span><span class="sxs-lookup"><span data-stu-id="fbfec-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="fbfec-108">[out] O número de bytes na retornado chave pública ou token.</span><span class="sxs-lookup"><span data-stu-id="fbfec-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="fbfec-109">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="fbfec-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="fbfec-110">[in] O tamanho, em caracteres largos, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="fbfec-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="fbfec-111">[out] Um ponteiro para o número de caracteres largos, na verdade, é retornado no `szName`.</span><span class="sxs-lookup"><span data-stu-id="fbfec-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="fbfec-112">[out] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="fbfec-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="fbfec-113">[out] Um ponteiro para o valor de hash.</span><span class="sxs-lookup"><span data-stu-id="fbfec-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="fbfec-114">Isso é o hash, usando o algoritmo SHA-1, do `PublicKey` propriedade do assembly referenciado, a menos que o arfFullOriginator do sinalizador do [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeração é definida.</span><span class="sxs-lookup"><span data-stu-id="fbfec-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="fbfec-115">[out] O número de caracteres largos no valor de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="fbfec-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="fbfec-116">[out] Um ponteiro para os sinalizadores que descrevem os metadados aplicados a um assembly.</span><span class="sxs-lookup"><span data-stu-id="fbfec-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="fbfec-117">O valor de sinalizadores é uma combinação de um ou mais [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores.</span><span class="sxs-lookup"><span data-stu-id="fbfec-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbfec-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fbfec-118">Return Value</span></span>  
 <span data-ttu-id="fbfec-119">Este método retorna S_OK se for bem-sucedida; Caso contrário, ele retorna um dos códigos de erro definidos no arquivo de cabeçalho Winerror. h.</span><span class="sxs-lookup"><span data-stu-id="fbfec-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbfec-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbfec-120">Requirements</span></span>  
 <span data-ttu-id="fbfec-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbfec-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbfec-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fbfec-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbfec-123">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fbfec-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fbfec-124">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fbfec-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fbfec-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbfec-125">See also</span></span>

- [<span data-ttu-id="fbfec-126">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="fbfec-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175961"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="921e0-102">Método IMetaDataAssemblyImport::GetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="921e0-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="921e0-103">Obtém o conjunto de propriedades para a referência de montagem com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="921e0-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="921e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="921e0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="921e0-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="921e0-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="921e0-106">[em] O `mdAssemblyRef` token de metadados que representa a referência de montagem para obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="921e0-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="921e0-107">[fora] Um ponteiro para a chave pública ou o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="921e0-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="921e0-108">[fora] O número de bytes na chave pública retornada ou token.</span><span class="sxs-lookup"><span data-stu-id="921e0-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="921e0-109">[fora] O nome simples da assembléia.</span><span class="sxs-lookup"><span data-stu-id="921e0-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="921e0-110">[em] O tamanho, em grandes `szName`chars, de .</span><span class="sxs-lookup"><span data-stu-id="921e0-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="921e0-111">[fora] Um ponteiro para o número de chars largos realmente retornou em `szName`.</span><span class="sxs-lookup"><span data-stu-id="921e0-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="921e0-112">[fora] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do conjunto.</span><span class="sxs-lookup"><span data-stu-id="921e0-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="921e0-113">[fora] Um ponteiro para o valor de hash.</span><span class="sxs-lookup"><span data-stu-id="921e0-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="921e0-114">Este é o hash, usando o algoritmo `PublicKey` SHA-1, da propriedade do conjunto que está sendo referenciada, a menos que a bandeira arfFullOriginator da enumeração [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) seja definida.</span><span class="sxs-lookup"><span data-stu-id="921e0-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="921e0-115">[fora] O número de chars largos no valor de hash devolvido.</span><span class="sxs-lookup"><span data-stu-id="921e0-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="921e0-116">[fora] Um ponteiro para bandeiras que descrevem os metadados aplicados a uma montagem.</span><span class="sxs-lookup"><span data-stu-id="921e0-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="921e0-117">O valor das bandeiras é uma combinação de um ou mais valores [corassemblyflags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="921e0-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="921e0-118">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="921e0-118">Return Value</span></span>  
 <span data-ttu-id="921e0-119">Este método retorna S_OK se for bem sucedido; caso contrário, ele retorna um dos códigos de erro definidos no arquivo winerror.h header.</span><span class="sxs-lookup"><span data-stu-id="921e0-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="921e0-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="921e0-120">Requirements</span></span>  
 <span data-ttu-id="921e0-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="921e0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="921e0-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="921e0-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="921e0-123">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="921e0-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="921e0-124">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="921e0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921e0-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="921e0-125">See also</span></span>

- [<span data-ttu-id="921e0-126">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="921e0-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

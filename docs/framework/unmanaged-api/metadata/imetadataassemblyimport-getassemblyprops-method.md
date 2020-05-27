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
ms.openlocfilehash: a90deaf3e9ddf326c6fca558cbb4681fc40e022d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009048"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="bef21-102">Método IMetaDataAssemblyImport::GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="bef21-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="bef21-103">Obtém o conjunto de propriedades para o assembly com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="bef21-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bef21-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bef21-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bef21-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="bef21-106">[in].</span><span class="sxs-lookup"><span data-stu-id="bef21-106">[in].</span></span> <span data-ttu-id="bef21-107">O `mdAssembly` token de metadados que representa o assembly para o qual obter as propriedades.</span><span class="sxs-lookup"><span data-stu-id="bef21-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="bef21-108">fora Um ponteiro para a chave pública ou o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="bef21-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="bef21-109">fora O número de bytes na chave pública retornada.</span><span class="sxs-lookup"><span data-stu-id="bef21-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="bef21-110">fora Um ponteiro para o algoritmo usado para fazer o hash dos arquivos no assembly.</span><span class="sxs-lookup"><span data-stu-id="bef21-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="bef21-111">fora O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="bef21-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bef21-112">no O tamanho, em caracteres largos, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="bef21-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="bef21-113">fora O número de caracteres largos realmente retornados em `szName` .</span><span class="sxs-lookup"><span data-stu-id="bef21-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="bef21-114">fora Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="bef21-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="bef21-115">fora Sinalizadores que descrevem os metadados aplicados a um assembly.</span><span class="sxs-lookup"><span data-stu-id="bef21-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="bef21-116">Esse valor é uma combinação de um ou mais valores de [CorAssemblyFlags](corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="bef21-116">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bef21-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bef21-117">Requirements</span></span>  
 <span data-ttu-id="bef21-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bef21-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bef21-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bef21-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bef21-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bef21-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bef21-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bef21-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef21-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="bef21-122">See also</span></span>

- [<span data-ttu-id="bef21-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="bef21-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)

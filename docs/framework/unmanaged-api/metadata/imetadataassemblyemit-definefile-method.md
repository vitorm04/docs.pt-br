---
title: Método IMetaDataAssemblyEmit::DefineFile
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6dac6bb6790876e28f1a5cd72f0635a1155caa47
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481034"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="48b50-102">Método IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="48b50-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="48b50-103">Cria um `File` estrutura de metadados que contém metadados de assembly referenciados por esse assembly e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="48b50-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48b50-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48b50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48b50-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="48b50-106">[in] O nome do arquivo a ser consumido.</span><span class="sxs-lookup"><span data-stu-id="48b50-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="48b50-107">[in] Um ponteiro para o hash de dados associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="48b50-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="48b50-108">[in] O tamanho em bytes do `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="48b50-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="48b50-109">[in] Uma combinação bit a bit de `FileFlags` valores que especificam as configurações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="48b50-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="48b50-110">[out] Um ponteiro para retornado `File` token.</span><span class="sxs-lookup"><span data-stu-id="48b50-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48b50-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="48b50-111">Remarks</span></span>  
 <span data-ttu-id="48b50-112">Um `File` estrutura de metadados deve ser definida para cada arquivo que foi parte desse assembly no momento em que este assembly foi compilado, excluindo o arquivo que contém os metadados.</span><span class="sxs-lookup"><span data-stu-id="48b50-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b50-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48b50-113">Requirements</span></span>  
 <span data-ttu-id="48b50-114">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48b50-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48b50-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="48b50-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48b50-116">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="48b50-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48b50-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48b50-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b50-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48b50-118">See also</span></span>
- [<span data-ttu-id="48b50-119">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="48b50-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

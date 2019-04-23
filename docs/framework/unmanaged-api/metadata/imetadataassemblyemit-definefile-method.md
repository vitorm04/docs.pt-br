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
ms.openlocfilehash: 5693da3b5e6d883efd9ad8a5a409a5dba8dd8b6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203425"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="3105b-102">Método IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="3105b-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="3105b-103">Cria um `File` estrutura de metadados que contém metadados de assembly referenciados por esse assembly e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="3105b-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3105b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3105b-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3105b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3105b-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3105b-106">[in] O nome do arquivo a ser consumido.</span><span class="sxs-lookup"><span data-stu-id="3105b-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3105b-107">[in] Um ponteiro para o hash de dados associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="3105b-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3105b-108">[in] O tamanho em bytes do `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="3105b-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="3105b-109">[in] Uma combinação bit a bit de `FileFlags` valores que especificam as configurações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3105b-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="3105b-110">[out] Um ponteiro para retornado `File` token.</span><span class="sxs-lookup"><span data-stu-id="3105b-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3105b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3105b-111">Remarks</span></span>  
 <span data-ttu-id="3105b-112">Um `File` estrutura de metadados deve ser definida para cada arquivo que foi parte desse assembly no momento em que este assembly foi compilado, excluindo o arquivo que contém os metadados.</span><span class="sxs-lookup"><span data-stu-id="3105b-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3105b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3105b-113">Requirements</span></span>  
 <span data-ttu-id="3105b-114">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3105b-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3105b-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3105b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3105b-116">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3105b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3105b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3105b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3105b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3105b-118">See also</span></span>

- [<span data-ttu-id="3105b-119">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="3105b-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

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
ms.openlocfilehash: 46fa6ab3ea4a63583b01ffe25d22840301613100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444790"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="925e6-102">Método IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="925e6-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="925e6-103">Cria um `File` estrutura de metadados que contém metadados para o assembly referenciado pelo assembly e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="925e6-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="925e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="925e6-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="925e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="925e6-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="925e6-106">[in] O nome do arquivo a ser consumido.</span><span class="sxs-lookup"><span data-stu-id="925e6-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="925e6-107">[in] Um ponteiro para o hash de dados associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="925e6-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="925e6-108">[in] O tamanho em bytes do `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="925e6-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="925e6-109">[in] Uma combinação bit a bit de `FileFlags` valores que especificam as configurações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="925e6-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="925e6-110">[out] Um ponteiro para retornado `File` token.</span><span class="sxs-lookup"><span data-stu-id="925e6-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="925e6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="925e6-111">Remarks</span></span>  
 <span data-ttu-id="925e6-112">Um `File` estrutura de metadados deve ser definida para cada arquivo que fazia parte desse assembly no momento em que este assembly foi compilado, excluindo o arquivo que contém os metadados.</span><span class="sxs-lookup"><span data-stu-id="925e6-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="925e6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="925e6-113">Requirements</span></span>  
 <span data-ttu-id="925e6-114">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="925e6-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="925e6-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="925e6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="925e6-116">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="925e6-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="925e6-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="925e6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="925e6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="925e6-118">See Also</span></span>  
 [<span data-ttu-id="925e6-119">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="925e6-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

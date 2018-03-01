---
title: "Método IMetaDataAssemblyEmit::DefineFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48584822d7a2f31c466401db3a24156a71ad7011
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="cb4d0-102">Método IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="cb4d0-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="cb4d0-103">Cria um `File` estrutura de metadados que contém metadados para o assembly referenciado pelo assembly e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="cb4d0-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb4d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb4d0-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb4d0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb4d0-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="cb4d0-106">[in] O nome do arquivo a ser consumido.</span><span class="sxs-lookup"><span data-stu-id="cb4d0-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="cb4d0-107">[in] Um ponteiro para o hash de dados associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="cb4d0-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="cb4d0-108">[in] O tamanho em bytes do `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="cb4d0-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="cb4d0-109">[in] Uma combinação bit a bit de `FileFlags` valores que especificam as configurações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="cb4d0-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="cb4d0-110">[out] Um ponteiro para retornado `File` token.</span><span class="sxs-lookup"><span data-stu-id="cb4d0-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb4d0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb4d0-111">Remarks</span></span>  
 <span data-ttu-id="cb4d0-112">Um `File` estrutura de metadados deve ser definida para cada arquivo que fazia parte desse assembly no momento em que este assembly foi compilado, excluindo o arquivo que contém os metadados.</span><span class="sxs-lookup"><span data-stu-id="cb4d0-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb4d0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb4d0-113">Requirements</span></span>  
 <span data-ttu-id="cb4d0-114">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb4d0-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb4d0-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb4d0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb4d0-116">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cb4d0-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb4d0-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb4d0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb4d0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb4d0-118">See Also</span></span>  
 [<span data-ttu-id="cb4d0-119">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="cb4d0-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

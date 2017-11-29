---
title: "Método IMetaDataAssemblyEmit::DefineAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 86002eb38d72ee628dbf54d0b5691f0816e6f996
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="5cc14-102">Método IMetaDataAssemblyEmit::DefineAssembly</span><span class="sxs-lookup"><span data-stu-id="5cc14-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="5cc14-103">Cria um `Assembly` estrutura que contém metadados para o assembly especificado e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="5cc14-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc14-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cc14-104">Syntax</span></span>  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cc14-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5cc14-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="5cc14-106">[in] A chave pública que identifica o Editor do assembly, ou nulo se o assembly não tem nome forte.</span><span class="sxs-lookup"><span data-stu-id="5cc14-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="5cc14-107">[in] O tamanho em bytes do `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="5cc14-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="5cc14-108">[in] O identificador do algoritmo de hash a ser usado para criptografar os arquivos de assembly ou nulo para especificar o algoritmo SHA-1.</span><span class="sxs-lookup"><span data-stu-id="5cc14-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="5cc14-109">[in] O nome de texto legível do assembly.</span><span class="sxs-lookup"><span data-stu-id="5cc14-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="5cc14-110">Esse valor não deve exceder 1024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="5cc14-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5cc14-111">[in] Um ponteiro para uma instância ASSEMBLYMETADATA que contém as informações de localidade, plataforma e versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="5cc14-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="5cc14-112">[in] Uma combinação de [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores que descrevem os recursos do assembly.</span><span class="sxs-lookup"><span data-stu-id="5cc14-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="5cc14-113">[out] Um ponteiro para o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="5cc14-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cc14-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="5cc14-114">Remarks</span></span>  
 <span data-ttu-id="5cc14-115">Apenas um `Assembly` estrutura de metadados pode ser definida em um manifesto.</span><span class="sxs-lookup"><span data-stu-id="5cc14-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cc14-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5cc14-116">Requirements</span></span>  
 <span data-ttu-id="5cc14-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cc14-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cc14-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5cc14-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cc14-119">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5cc14-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5cc14-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cc14-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc14-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cc14-121">See Also</span></span>  
 [<span data-ttu-id="5cc14-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="5cc14-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

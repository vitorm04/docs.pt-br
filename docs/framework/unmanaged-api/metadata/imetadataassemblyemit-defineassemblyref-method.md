---
title: Método IMetaDataAssemblyEmit::DefineAssemblyRef
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e480c408c10eb9e135f260426750f7747e5d8ce5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117346"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="7e33e-102">Método IMetaDataAssemblyEmit::DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="7e33e-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="7e33e-103">Cria um `AssemblyRef` estrutura que contém metadados para o assembly que faz referência a esse assembly e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="7e33e-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e33e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e33e-104">Syntax</span></span>  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e33e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e33e-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="7e33e-106">[in] A chave pública do Editor do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="7e33e-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="7e33e-107">A função auxiliar [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) pode ser usado para obter o hash da chave pública para passar como este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7e33e-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="7e33e-108">[in] O tamanho em bytes do `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="7e33e-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="7e33e-109">[in] O nome de texto legível do assembly.</span><span class="sxs-lookup"><span data-stu-id="7e33e-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="7e33e-110">Esse valor não deve exceder 1024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="7e33e-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="7e33e-111">[in] Uma instância ASSEMBLYMETADATA que contém as informações de versão, a plataforma e a localidade do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="7e33e-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="7e33e-112">[in] O hash de dados associados ao assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="7e33e-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="7e33e-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7e33e-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="7e33e-114">[in] O tamanho em bytes do `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="7e33e-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="7e33e-115">[in] Uma combinação bit a bit de [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores que influenciam o comportamento do mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="7e33e-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="7e33e-116">[out] Um ponteiro para retornado `AssemblyRef` token de metadados.</span><span class="sxs-lookup"><span data-stu-id="7e33e-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e33e-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e33e-117">Remarks</span></span>  
 <span data-ttu-id="7e33e-118">Um `AssemblyRef` estrutura de metadados deve ser definida para cada assembly que faz referência a esse assembly.</span><span class="sxs-lookup"><span data-stu-id="7e33e-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="7e33e-119">Em tempo de execução, os detalhes de um assembly referenciado são passados para o resolvedor de assembly com uma indicação de que eles representam as informações "no estado criado".</span><span class="sxs-lookup"><span data-stu-id="7e33e-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="7e33e-120">O resolvedor de assembly, em seguida, aplica a política.</span><span class="sxs-lookup"><span data-stu-id="7e33e-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e33e-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e33e-121">Requirements</span></span>  
 <span data-ttu-id="7e33e-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e33e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e33e-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e33e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e33e-124">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7e33e-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7e33e-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7e33e-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e33e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e33e-126">See also</span></span>

- [<span data-ttu-id="7e33e-127">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="7e33e-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

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
ms.openlocfilehash: c88b7a401a19b1bd0e02edab7ef7bbee1372199e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432084"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="6c1ea-102">Método IMetaDataAssemblyEmit::DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="6c1ea-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="6c1ea-103">Cria uma estrutura de `AssemblyRef` que contém metadados para o assembly ao qual este assembly faz referência e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c1ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c1ea-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="6c1ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c1ea-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="6c1ea-106">no A chave pública do Publicador do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="6c1ea-107">A função auxiliar [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) pode ser usada para obter o hash da chave pública a ser passada como esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="6c1ea-108">no O tamanho em bytes de `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="6c1ea-109">no O nome de texto legível por humanos do assembly.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="6c1ea-110">Esse valor não deve exceder 1024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="6c1ea-111">no Uma instância de ASSEMBLYMETADATA que contém a versão, a plataforma e as informações de localidade do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="6c1ea-112">no Os dados de hash associados ao assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="6c1ea-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="6c1ea-114">no O tamanho em bytes de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="6c1ea-115">no Uma combinação bits de valores [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) que influencia o comportamento do mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="6c1ea-116">fora Um ponteiro para o token de metadados de `AssemblyRef` retornado.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c1ea-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c1ea-117">Remarks</span></span>  
 <span data-ttu-id="6c1ea-118">Uma estrutura de metadados `AssemblyRef` deve ser definida para cada assembly referenciado por esse assembly.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="6c1ea-119">Em tempo de execução, os detalhes de um assembly referenciado são passados para o resolvedor de assembly com uma indicação de que eles representam as informações "como criadas".</span><span class="sxs-lookup"><span data-stu-id="6c1ea-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="6c1ea-120">Em seguida, o resolvedor de assembly aplica a política.</span><span class="sxs-lookup"><span data-stu-id="6c1ea-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c1ea-121">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6c1ea-121">Requirements</span></span>  
 <span data-ttu-id="6c1ea-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c1ea-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c1ea-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6c1ea-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c1ea-124">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c1ea-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c1ea-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c1ea-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c1ea-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c1ea-126">See also</span></span>

- [<span data-ttu-id="6c1ea-127">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="6c1ea-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

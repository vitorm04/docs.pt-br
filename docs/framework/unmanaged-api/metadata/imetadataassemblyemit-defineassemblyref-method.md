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
ms.openlocfilehash: 612463bca18c23fac0b086adde2d208a0fbc5ae5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008161"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="5edc7-102">Método IMetaDataAssemblyEmit::DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="5edc7-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="5edc7-103">Cria uma `AssemblyRef` estrutura que contém metadados para o assembly ao qual este assembly faz referência e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="5edc7-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5edc7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5edc7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5edc7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5edc7-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="5edc7-106">no A chave pública do Publicador do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="5edc7-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="5edc7-107">A função auxiliar [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) pode ser usada para obter o hash da chave pública a ser passada como esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5edc7-107">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="5edc7-108">no O tamanho em bytes de `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="5edc7-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="5edc7-109">no O nome de texto legível por humanos do assembly.</span><span class="sxs-lookup"><span data-stu-id="5edc7-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="5edc7-110">Esse valor não deve exceder 1024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="5edc7-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5edc7-111">no Uma instância de ASSEMBLYMETADATA que contém a versão, a plataforma e as informações de localidade do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="5edc7-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="5edc7-112">no Os dados de hash associados ao assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="5edc7-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="5edc7-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5edc7-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="5edc7-114">no O tamanho em bytes de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="5edc7-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="5edc7-115">no Uma combinação bits de valores [CorAssemblyFlags](corassemblyflags-enumeration.md) que influencia o comportamento do mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="5edc7-115">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="5edc7-116">fora Um ponteiro para o `AssemblyRef` token de metadados retornado.</span><span class="sxs-lookup"><span data-stu-id="5edc7-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5edc7-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="5edc7-117">Remarks</span></span>  
 <span data-ttu-id="5edc7-118">Uma `AssemblyRef` estrutura de metadados deve ser definida para cada assembly referenciado por esse assembly.</span><span class="sxs-lookup"><span data-stu-id="5edc7-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="5edc7-119">Em tempo de execução, os detalhes de um assembly referenciado são passados para o resolvedor de assembly com uma indicação de que eles representam as informações "como criadas".</span><span class="sxs-lookup"><span data-stu-id="5edc7-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="5edc7-120">Em seguida, o resolvedor de assembly aplica a política.</span><span class="sxs-lookup"><span data-stu-id="5edc7-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5edc7-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5edc7-121">Requirements</span></span>  
 <span data-ttu-id="5edc7-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5edc7-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5edc7-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5edc7-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5edc7-124">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5edc7-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5edc7-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5edc7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5edc7-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="5edc7-126">See also</span></span>

- [<span data-ttu-id="5edc7-127">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="5edc7-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

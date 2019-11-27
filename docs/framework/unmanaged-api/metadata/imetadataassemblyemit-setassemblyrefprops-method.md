---
title: Método IMetaDataAssemblyEmit::SetAssemblyRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: 5434aa2d12bd9a29a8c2fc784421442469ceb1ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440553"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="6d94c-102">Método IMetaDataAssemblyEmit::SetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="6d94c-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="6d94c-103">Modifica a estrutura de metadados de `AssemblyRef` especificada.</span><span class="sxs-lookup"><span data-stu-id="6d94c-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d94c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d94c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d94c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d94c-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="6d94c-106">no O token de metadados que especifica a estrutura de metadados `AssemblyRef` a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="6d94c-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="6d94c-107">no A chave pública do Publicador do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="6d94c-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="6d94c-108">no O tamanho em bytes de `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="6d94c-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="6d94c-109">no O nome de texto legível por humanos do assembly.</span><span class="sxs-lookup"><span data-stu-id="6d94c-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="6d94c-110">no Um ponteiro para uma instância ASSEMBLYMETADATA que contém a versão, a plataforma e as informações de localidade para o assembly.</span><span class="sxs-lookup"><span data-stu-id="6d94c-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="6d94c-111">no Um ponteiro para os dados de hash associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="6d94c-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="6d94c-112">no O tamanho em bytes de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="6d94c-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="6d94c-113">no Uma combinação de bits de valores [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) que especifica atributos do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="6d94c-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d94c-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d94c-114">Remarks</span></span>  
 <span data-ttu-id="6d94c-115">Para criar uma estrutura de metadados `AssemblyRef`, use o método [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d94c-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d94c-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6d94c-116">Requirements</span></span>  
 <span data-ttu-id="6d94c-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d94c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d94c-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6d94c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d94c-119">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6d94c-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d94c-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d94c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d94c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d94c-121">See also</span></span>

- [<span data-ttu-id="6d94c-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="6d94c-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

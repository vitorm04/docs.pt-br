---
title: Método IMetaDataAssemblyEmit::SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: f79320d5b7d2ad4ad44a79fae063ce6718490a70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431954"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="25e01-102">Método IMetaDataAssemblyEmit::SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="25e01-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="25e01-103">Modifica a estrutura de metadados de `Assembly` especificada.</span><span class="sxs-lookup"><span data-stu-id="25e01-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25e01-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25e01-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25e01-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25e01-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="25e01-106">no O token de metadados que especifica a estrutura de metadados `Assembly` a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="25e01-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="25e01-107">no Um ponteiro para a chave pública do Publicador do assembly.</span><span class="sxs-lookup"><span data-stu-id="25e01-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="25e01-108">no O tamanho em bytes de `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="25e01-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="25e01-109">no O identificador do algoritmo de hash usado para fazer o hash dos arquivos de assembly.</span><span class="sxs-lookup"><span data-stu-id="25e01-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="25e01-110">no O nome de texto legível por humanos do assembly.</span><span class="sxs-lookup"><span data-stu-id="25e01-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="25e01-111">no Um ponteiro para o ASSEMBLYMETADATA que contém informações de versão, plataforma e localidade para o assembly.</span><span class="sxs-lookup"><span data-stu-id="25e01-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="25e01-112">no Uma combinação de bits de valores [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) que especifica vários atributos do assembly.</span><span class="sxs-lookup"><span data-stu-id="25e01-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25e01-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="25e01-113">Remarks</span></span>  
 <span data-ttu-id="25e01-114">Para criar uma estrutura de metadados `Assembly`, use o método [IMetaDataAssemblyEmit::D efineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="25e01-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25e01-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="25e01-115">Requirements</span></span>  
 <span data-ttu-id="25e01-116">**Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25e01-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25e01-117">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="25e01-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25e01-118">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="25e01-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25e01-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25e01-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e01-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25e01-120">See also</span></span>

- [<span data-ttu-id="25e01-121">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="25e01-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

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
ms.openlocfilehash: fb381a872cbeb787da0c6920f2cdeef434fb33ea
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008086"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="ede84-102">Método IMetaDataAssemblyEmit::SetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="ede84-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="ede84-103">Modifica a estrutura de `AssemblyRef` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="ede84-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ede84-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ede84-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ede84-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="ede84-106">no O token de metadados que especifica a `AssemblyRef` estrutura de metadados a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="ede84-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="ede84-107">no A chave pública do Publicador do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="ede84-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="ede84-108">no O tamanho em bytes de `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="ede84-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="ede84-109">no O nome de texto legível por humanos do assembly.</span><span class="sxs-lookup"><span data-stu-id="ede84-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="ede84-110">no Um ponteiro para uma instância ASSEMBLYMETADATA que contém a versão, a plataforma e as informações de localidade para o assembly.</span><span class="sxs-lookup"><span data-stu-id="ede84-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="ede84-111">no Um ponteiro para os dados de hash associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="ede84-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="ede84-112">no O tamanho em bytes de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="ede84-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="ede84-113">no Uma combinação de bits de valores [AssemblyRefFlags](assemblyrefflags-enumeration.md) que especifica atributos do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="ede84-113">[in] A bitwise combination of [AssemblyRefFlags](assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ede84-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="ede84-114">Remarks</span></span>  
 <span data-ttu-id="ede84-115">Para criar uma `AssemblyRef` estrutura de metadados, use o método [IMetaDataAssemblyEmit::D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ede84-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede84-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ede84-116">Requirements</span></span>  
 <span data-ttu-id="ede84-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede84-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede84-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ede84-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ede84-119">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ede84-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ede84-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede84-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede84-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="ede84-121">See also</span></span>

- [<span data-ttu-id="ede84-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="ede84-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

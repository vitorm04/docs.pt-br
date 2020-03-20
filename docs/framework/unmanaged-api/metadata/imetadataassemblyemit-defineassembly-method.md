---
title: Método IMetaDataAssemblyEmit::DefineAssembly
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177895"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="1ec68-102">Método IMetaDataAssemblyEmit::DefineAssembly</span><span class="sxs-lookup"><span data-stu-id="1ec68-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="1ec68-103">Cria `Assembly` uma estrutura contendo metadados para o conjunto especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="1ec68-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ec68-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="1ec68-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ec68-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="1ec68-106">[em] A chave pública que identifica o editor da montagem, ou NULL se a montagem não for fortemente nomeada.</span><span class="sxs-lookup"><span data-stu-id="1ec68-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="1ec68-107">[em] O tamanho em bytes de `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="1ec68-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="1ec68-108">[em] O identificador do algoritmo de hashing para usar para criptografar os arquivos no conjunto, ou NULL para especificar o algoritmo SHA-1.</span><span class="sxs-lookup"><span data-stu-id="1ec68-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="1ec68-109">[em] O nome de texto de leitura humana da assembléia.</span><span class="sxs-lookup"><span data-stu-id="1ec68-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="1ec68-110">Este valor não deve exceder 1024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="1ec68-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="1ec68-111">[em] Um ponteiro para uma instância ASSEMBLYMETADATA que contém as informações de versão, plataforma e local para o conjunto.</span><span class="sxs-lookup"><span data-stu-id="1ec68-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="1ec68-112">[em] Uma combinação de valores [corassemblyflags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) que descrevem características do conjunto.</span><span class="sxs-lookup"><span data-stu-id="1ec68-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="1ec68-113">[fora] Um ponteiro para o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="1ec68-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ec68-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ec68-114">Remarks</span></span>  
 <span data-ttu-id="1ec68-115">Apenas `Assembly` uma estrutura de metadados pode ser definida dentro de um manifesto.</span><span class="sxs-lookup"><span data-stu-id="1ec68-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ec68-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ec68-116">Requirements</span></span>  
 <span data-ttu-id="1ec68-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ec68-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ec68-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ec68-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ec68-119">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ec68-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ec68-120">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ec68-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec68-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ec68-121">See also</span></span>

- [<span data-ttu-id="1ec68-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="1ec68-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

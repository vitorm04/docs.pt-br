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
ms.openlocfilehash: 17c91200730431c4c6e230b8c1561ce7c4863868
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008177"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="88208-102">Método IMetaDataAssemblyEmit::DefineAssembly</span><span class="sxs-lookup"><span data-stu-id="88208-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="88208-103">Cria uma `Assembly` estrutura que contém metadados para o assembly especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="88208-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88208-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88208-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="88208-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88208-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="88208-106">no A chave pública que identifica o editor do assembly ou NULL se o assembly não tiver um nome forte.</span><span class="sxs-lookup"><span data-stu-id="88208-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="88208-107">no O tamanho em bytes de `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="88208-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="88208-108">no O identificador do algoritmo de hash a ser usado para criptografar os arquivos no assembly ou nulo para especificar o algoritmo SHA-1.</span><span class="sxs-lookup"><span data-stu-id="88208-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="88208-109">no O nome de texto legível por humanos do assembly.</span><span class="sxs-lookup"><span data-stu-id="88208-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="88208-110">Esse valor não deve exceder 1024 caracteres.</span><span class="sxs-lookup"><span data-stu-id="88208-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="88208-111">no Um ponteiro para uma instância ASSEMBLYMETADATA que contém a versão, a plataforma e as informações de localidade para o assembly.</span><span class="sxs-lookup"><span data-stu-id="88208-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="88208-112">no Uma combinação de valores [CorAssemblyFlags](corassemblyflags-enumeration.md) que descrevem os recursos do assembly.</span><span class="sxs-lookup"><span data-stu-id="88208-112">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="88208-113">fora Um ponteiro para o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="88208-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88208-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="88208-114">Remarks</span></span>  
 <span data-ttu-id="88208-115">Somente uma `Assembly` estrutura de metadados pode ser definida em um manifesto.</span><span class="sxs-lookup"><span data-stu-id="88208-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88208-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88208-116">Requirements</span></span>  
 <span data-ttu-id="88208-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88208-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88208-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="88208-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88208-119">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88208-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88208-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88208-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88208-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="88208-121">See also</span></span>

- [<span data-ttu-id="88208-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="88208-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

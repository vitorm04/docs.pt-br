---
title: Método IMetaDataAssemblyEmit::DefineFile
ms.date: 03/30/2017
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
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176052"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="1ad05-102">Método IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="1ad05-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="1ad05-103">Cria `File` uma estrutura de metadados contendo metadados para montagem referenciada por este conjunto e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="1ad05-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ad05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ad05-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ad05-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ad05-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1ad05-106">[em] O nome do arquivo a ser consumido.</span><span class="sxs-lookup"><span data-stu-id="1ad05-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="1ad05-107">[em] Um ponteiro para os dados de hash associados à montagem.</span><span class="sxs-lookup"><span data-stu-id="1ad05-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="1ad05-108">[em] O tamanho em bytes de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="1ad05-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="1ad05-109">[em] Uma combinação bitwise de `FileFlags` valores que especificam configurações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="1ad05-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="1ad05-110">[fora] Um ponteiro para `File` o token devolvido.</span><span class="sxs-lookup"><span data-stu-id="1ad05-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ad05-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ad05-111">Remarks</span></span>  
 <span data-ttu-id="1ad05-112">Uma `File` estrutura de metadados deve ser definida para cada arquivo que fazia parte desta montagem no momento em que este conjunto foi construído, excluindo o arquivo que contém os metadados.</span><span class="sxs-lookup"><span data-stu-id="1ad05-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ad05-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ad05-113">Requirements</span></span>  
 <span data-ttu-id="1ad05-114">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ad05-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ad05-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ad05-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ad05-116">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ad05-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ad05-117">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ad05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad05-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ad05-118">See also</span></span>

- [<span data-ttu-id="1ad05-119">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="1ad05-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

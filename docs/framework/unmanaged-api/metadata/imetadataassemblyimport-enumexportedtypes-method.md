---
title: Método IMetaDataAssemblyImport::EnumExportedTypes
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176000"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="7acd6-102">Método IMetaDataAssemblyImport::EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="7acd6-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="7acd6-103">Enumera os tipos exportados referenciados no manifesto de montagem no escopo de metadados atuais.</span><span class="sxs-lookup"><span data-stu-id="7acd6-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7acd6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7acd6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7acd6-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="7acd6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7acd6-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="7acd6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7acd6-107">Este deve ser um `EnumExportedTypes` valor nulo quando o método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="7acd6-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="7acd6-108">[fora] A enumeração `mdExportedType` de tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="7acd6-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7acd6-109">[em] O número `mdExportedType` máximo de tokens que `rExportedTypes` podem ser colocados na matriz.</span><span class="sxs-lookup"><span data-stu-id="7acd6-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7acd6-110">[fora] O número `mdExportedType` de tokens `rExportedTypes`realmente colocados em .</span><span class="sxs-lookup"><span data-stu-id="7acd6-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7acd6-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7acd6-111">Return Value</span></span>  
  
|<span data-ttu-id="7acd6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7acd6-112">HRESULT</span></span>|<span data-ttu-id="7acd6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7acd6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7acd6-114">`EnumExportedTypes`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="7acd6-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7acd6-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="7acd6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7acd6-116">Neste caso, `pcTokens` está definido como zero.</span><span class="sxs-lookup"><span data-stu-id="7acd6-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7acd6-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7acd6-117">Requirements</span></span>  
 <span data-ttu-id="7acd6-118">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7acd6-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7acd6-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7acd6-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7acd6-120">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7acd6-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7acd6-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7acd6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7acd6-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7acd6-122">See also</span></span>

- [<span data-ttu-id="7acd6-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="7acd6-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)

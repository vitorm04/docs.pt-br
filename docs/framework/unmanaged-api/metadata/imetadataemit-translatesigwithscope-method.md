---
title: Método IMetaDataEmit::TranslateSigWithScope
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: 2662af41fbd2cdc3ce8a6df1e036dfc5b22ff6a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175537"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="1be8d-102">Método IMetaDataEmit::TranslateSigWithScope</span><span class="sxs-lookup"><span data-stu-id="1be8d-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="1be8d-103">Importa uma montagem no escopo atual e obtém uma nova assinatura de metadados para o escopo mesclado.</span><span class="sxs-lookup"><span data-stu-id="1be8d-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be8d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1be8d-104">Syntax</span></span>  
  
```cpp  
HRESULT TranslateSigWithScope (
    [in]  IMetaDataAssemblyImport   *pAssemImport,
    [in]  const void                *pbHashValue,
    [in]  ULONG                     cbHashValue,
    [in]  IMetaDataImport           *import,
    [in]  PCCOR_SIGNATURE           pbSigBlob,
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,
    [in]  IMetaDataEmit             *emit,
    [out] PCOR_SIGNATURE            pvTranslatedSig,
    [in]  ULONG                     cbTranslatedSigMax,
    [out] ULONG                     *pcbTranslatedSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1be8d-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="1be8d-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="1be8d-106">[em] A interface para montagem de importação (onde a assinatura é definida).</span><span class="sxs-lookup"><span data-stu-id="1be8d-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="1be8d-107">[em] A bolha de hash para a assembléia.</span><span class="sxs-lookup"><span data-stu-id="1be8d-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="1be8d-108">[em] A contagem de `pbHashValue`bytes em .</span><span class="sxs-lookup"><span data-stu-id="1be8d-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="1be8d-109">[em] A interface para escopo de metadados de importação.</span><span class="sxs-lookup"><span data-stu-id="1be8d-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="1be8d-110">[em] A assinatura a ser importada.</span><span class="sxs-lookup"><span data-stu-id="1be8d-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="1be8d-111">[em] O tamanho, em bytes, de `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="1be8d-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="1be8d-112">[em] A interface para montagem de exportação.</span><span class="sxs-lookup"><span data-stu-id="1be8d-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="1be8d-113">[em] A interface para escopo de metadados de exportação.</span><span class="sxs-lookup"><span data-stu-id="1be8d-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="1be8d-114">[fora] O buffer para segurar a bolha de assinatura traduzida.</span><span class="sxs-lookup"><span data-stu-id="1be8d-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="1be8d-115">[em] A capacidade, em bytes, de `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="1be8d-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="1be8d-116">[fora] O número de bytes reais na assinatura traduzida.</span><span class="sxs-lookup"><span data-stu-id="1be8d-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1be8d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1be8d-117">Requirements</span></span>  
 <span data-ttu-id="1be8d-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1be8d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1be8d-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1be8d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1be8d-120">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1be8d-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1be8d-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1be8d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be8d-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="1be8d-122">See also</span></span>

- [<span data-ttu-id="1be8d-123">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="1be8d-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="1be8d-124">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="1be8d-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="1be8d-125">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1be8d-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1be8d-126">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1be8d-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="1be8d-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="1be8d-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

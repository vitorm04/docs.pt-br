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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e03572a4eaa0251866e8bfc6ae2d01d955d7b8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516181"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="46246-102">Método IMetaDataEmit::TranslateSigWithScope</span><span class="sxs-lookup"><span data-stu-id="46246-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="46246-103">Importa um assembly para o escopo atual e obtém uma nova assinatura de metadados para o escopo mesclado.</span><span class="sxs-lookup"><span data-stu-id="46246-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46246-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46246-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="46246-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="46246-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="46246-106">[in] A interface para o assembly de importação (em que a assinatura é definida).</span><span class="sxs-lookup"><span data-stu-id="46246-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="46246-107">[in] O blob de hash para o assembly.</span><span class="sxs-lookup"><span data-stu-id="46246-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="46246-108">[in] A contagem de bytes em `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="46246-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="46246-109">[in] A interface para o escopo de metadados de importação.</span><span class="sxs-lookup"><span data-stu-id="46246-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="46246-110">[in] A assinatura a ser importado.</span><span class="sxs-lookup"><span data-stu-id="46246-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="46246-111">[in] O tamanho, em bytes, do `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="46246-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="46246-112">[in] A interface para o assembly de exportação.</span><span class="sxs-lookup"><span data-stu-id="46246-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="46246-113">[in] A interface para o escopo de metadados de exportação.</span><span class="sxs-lookup"><span data-stu-id="46246-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="46246-114">[out] O buffer para armazenar o blob de assinatura traduzido.</span><span class="sxs-lookup"><span data-stu-id="46246-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="46246-115">[in] A capacidade, em bytes, do `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="46246-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="46246-116">[out] O número de bytes reais na assinatura traduzida.</span><span class="sxs-lookup"><span data-stu-id="46246-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46246-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46246-117">Requirements</span></span>  
 <span data-ttu-id="46246-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46246-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46246-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="46246-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46246-120">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="46246-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46246-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46246-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46246-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46246-122">See also</span></span>
- [<span data-ttu-id="46246-123">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="46246-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="46246-124">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="46246-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="46246-125">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="46246-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="46246-126">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="46246-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="46246-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="46246-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

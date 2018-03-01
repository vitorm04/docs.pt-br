---
title: "Método IMetaDataEmit::TranslateSigWithScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ceb6a8bfbee5823e7080d8c98647da93a10a5b79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="61e90-102">Método IMetaDataEmit::TranslateSigWithScope</span><span class="sxs-lookup"><span data-stu-id="61e90-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="61e90-103">Importa um assembly para o escopo atual e obtém uma nova assinatura de metadados para o escopo mesclado.</span><span class="sxs-lookup"><span data-stu-id="61e90-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e90-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61e90-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="61e90-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61e90-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="61e90-106">[in] A interface para o assembly de importação (onde a assinatura é definida).</span><span class="sxs-lookup"><span data-stu-id="61e90-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="61e90-107">[in] O blob de hash para o assembly.</span><span class="sxs-lookup"><span data-stu-id="61e90-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="61e90-108">[in] A contagem de bytes em `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="61e90-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="61e90-109">[in] A interface para o escopo de metadados de importação.</span><span class="sxs-lookup"><span data-stu-id="61e90-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="61e90-110">[in] A assinatura a ser importado.</span><span class="sxs-lookup"><span data-stu-id="61e90-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="61e90-111">[in] O tamanho, em bytes, de `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="61e90-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="61e90-112">[in] A interface para o assembly de exportação.</span><span class="sxs-lookup"><span data-stu-id="61e90-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="61e90-113">[in] A interface para o escopo de metadados de exportação.</span><span class="sxs-lookup"><span data-stu-id="61e90-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="61e90-114">[out] O buffer para armazenar o blob de assinatura traduzidos.</span><span class="sxs-lookup"><span data-stu-id="61e90-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="61e90-115">[in] A capacidade, em bytes, de `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="61e90-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="61e90-116">[out] O número de bytes reais na assinatura traduzida.</span><span class="sxs-lookup"><span data-stu-id="61e90-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61e90-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61e90-117">Requirements</span></span>  
 <span data-ttu-id="61e90-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61e90-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61e90-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61e90-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61e90-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="61e90-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61e90-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61e90-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e90-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61e90-122">See Also</span></span>  
 [<span data-ttu-id="61e90-123">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="61e90-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="61e90-124">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="61e90-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="61e90-125">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="61e90-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="61e90-126">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="61e90-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="61e90-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="61e90-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

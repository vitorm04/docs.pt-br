---
title: "Método IMetaDataImport::GetSigFromToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetSigFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6328e112aa948ecc2f0f5d816c4fd77673e06244
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="70bd4-102">Método IMetaDataImport::GetSigFromToken</span><span class="sxs-lookup"><span data-stu-id="70bd4-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="70bd4-103">Obtém a assinatura de binários de metadados associada ao token especificado.</span><span class="sxs-lookup"><span data-stu-id="70bd4-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70bd4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70bd4-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70bd4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70bd4-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="70bd4-106">[in] O token para retornar a assinatura de metadados binário para.</span><span class="sxs-lookup"><span data-stu-id="70bd4-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="70bd4-107">[out] Um ponteiro para a assinatura de metadados retornados.</span><span class="sxs-lookup"><span data-stu-id="70bd4-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="70bd4-108">[out] O tamanho em bytes da assinatura de metadados binário.</span><span class="sxs-lookup"><span data-stu-id="70bd4-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70bd4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70bd4-109">Requirements</span></span>  
 <span data-ttu-id="70bd4-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70bd4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70bd4-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70bd4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70bd4-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="70bd4-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70bd4-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70bd4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bd4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70bd4-114">See Also</span></span>  
 [<span data-ttu-id="70bd4-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="70bd4-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="70bd4-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="70bd4-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

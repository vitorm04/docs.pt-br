---
title: Método IMetaDataImport::GetSigFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 823a172c05d2ce76fef790966f54d7216f579fde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152978"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="c3558-102">Método IMetaDataImport::GetSigFromToken</span><span class="sxs-lookup"><span data-stu-id="c3558-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="c3558-103">Obtém a assinatura binária metadados associada com o token especificado.</span><span class="sxs-lookup"><span data-stu-id="c3558-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3558-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3558-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3558-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3558-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="c3558-106">[in] O token para retornar a assinatura de metadados de binários para.</span><span class="sxs-lookup"><span data-stu-id="c3558-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="c3558-107">[out] Um ponteiro para a assinatura de metadados retornados.</span><span class="sxs-lookup"><span data-stu-id="c3558-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="c3558-108">[out] O tamanho em bytes da assinatura de metadados de binário.</span><span class="sxs-lookup"><span data-stu-id="c3558-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3558-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3558-109">Requirements</span></span>  
 <span data-ttu-id="c3558-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3558-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3558-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3558-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3558-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c3558-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c3558-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c3558-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3558-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3558-114">See also</span></span>

- [<span data-ttu-id="c3558-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c3558-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c3558-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c3558-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

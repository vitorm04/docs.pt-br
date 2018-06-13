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
ms.openlocfilehash: f40fb2e94eac13211cf8ccf179904071a23f59ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447221"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="ad451-102">Método IMetaDataImport::GetSigFromToken</span><span class="sxs-lookup"><span data-stu-id="ad451-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="ad451-103">Obtém a assinatura de binários de metadados associada ao token especificado.</span><span class="sxs-lookup"><span data-stu-id="ad451-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad451-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad451-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad451-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad451-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="ad451-106">[in] O token para retornar a assinatura de metadados binário para.</span><span class="sxs-lookup"><span data-stu-id="ad451-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="ad451-107">[out] Um ponteiro para a assinatura de metadados retornados.</span><span class="sxs-lookup"><span data-stu-id="ad451-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="ad451-108">[out] O tamanho em bytes da assinatura de metadados binário.</span><span class="sxs-lookup"><span data-stu-id="ad451-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad451-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad451-109">Requirements</span></span>  
 <span data-ttu-id="ad451-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad451-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad451-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad451-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad451-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ad451-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad451-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad451-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad451-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad451-114">See Also</span></span>  
 [<span data-ttu-id="ad451-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ad451-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ad451-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ad451-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

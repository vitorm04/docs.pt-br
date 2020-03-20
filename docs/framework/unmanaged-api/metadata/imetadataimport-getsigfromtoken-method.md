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
ms.openlocfilehash: 5af59e158a34b06d304a98db1dfaa46585b22eb6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177203"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="b7bde-102">Método IMetaDataImport::GetSigFromToken</span><span class="sxs-lookup"><span data-stu-id="b7bde-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="b7bde-103">Obtém a assinatura binária de metadados associada ao token especificado.</span><span class="sxs-lookup"><span data-stu-id="b7bde-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7bde-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7bde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7bde-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7bde-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="b7bde-106">[em] O token para retornar a assinatura binária de metadados para.</span><span class="sxs-lookup"><span data-stu-id="b7bde-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="b7bde-107">[fora] Um ponteiro para a assinatura de metadados retornado.</span><span class="sxs-lookup"><span data-stu-id="b7bde-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="b7bde-108">[fora] O tamanho em bytes da assinatura binária de metadados.</span><span class="sxs-lookup"><span data-stu-id="b7bde-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7bde-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7bde-109">Requirements</span></span>  
 <span data-ttu-id="b7bde-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7bde-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7bde-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b7bde-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7bde-112">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7bde-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7bde-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7bde-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7bde-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7bde-114">See also</span></span>

- [<span data-ttu-id="b7bde-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b7bde-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b7bde-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b7bde-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

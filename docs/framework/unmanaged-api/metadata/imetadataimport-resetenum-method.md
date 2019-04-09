---
title: Método IMetaDataImport::ResetEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 143b11f0a99081b7d49bfbb68b635d92cf1e9ba3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163872"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="31e79-102">Método IMetaDataImport::ResetEnum</span><span class="sxs-lookup"><span data-stu-id="31e79-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="31e79-103">Redefine o enumerador especificado na posição especificada.</span><span class="sxs-lookup"><span data-stu-id="31e79-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e79-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31e79-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31e79-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31e79-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="31e79-106">[in] O enumerador para redefinir.</span><span class="sxs-lookup"><span data-stu-id="31e79-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="31e79-107">[in] A nova posição na qual colocar o enumerador.</span><span class="sxs-lookup"><span data-stu-id="31e79-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e79-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31e79-108">Requirements</span></span>  
 <span data-ttu-id="31e79-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31e79-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e79-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31e79-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31e79-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="31e79-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="31e79-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="31e79-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="31e79-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31e79-113">See also</span></span>

- [<span data-ttu-id="31e79-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="31e79-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="31e79-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="31e79-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

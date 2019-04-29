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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777423"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="c4b08-102">Método IMetaDataImport::ResetEnum</span><span class="sxs-lookup"><span data-stu-id="c4b08-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="c4b08-103">Redefine o enumerador especificado na posição especificada.</span><span class="sxs-lookup"><span data-stu-id="c4b08-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4b08-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4b08-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4b08-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="c4b08-106">[in] O enumerador para redefinir.</span><span class="sxs-lookup"><span data-stu-id="c4b08-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="c4b08-107">[in] A nova posição na qual colocar o enumerador.</span><span class="sxs-lookup"><span data-stu-id="c4b08-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b08-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4b08-108">Requirements</span></span>  
 <span data-ttu-id="c4b08-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4b08-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b08-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c4b08-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4b08-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c4b08-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4b08-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b08-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b08-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4b08-113">See also</span></span>

- [<span data-ttu-id="c4b08-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c4b08-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c4b08-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c4b08-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

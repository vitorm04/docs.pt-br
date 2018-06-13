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
ms.openlocfilehash: 56fc0273fb2c1b77c74d7a1d853886f47170497e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447922"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="2a0e4-102">Método IMetaDataImport::ResetEnum</span><span class="sxs-lookup"><span data-stu-id="2a0e4-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="2a0e4-103">Redefine o enumerador especificado para a posição especificada.</span><span class="sxs-lookup"><span data-stu-id="2a0e4-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a0e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a0e4-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a0e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a0e4-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="2a0e4-106">[in] O enumerador para redefinir.</span><span class="sxs-lookup"><span data-stu-id="2a0e4-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="2a0e4-107">[in] A nova posição na qual colocar o enumerador.</span><span class="sxs-lookup"><span data-stu-id="2a0e4-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a0e4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a0e4-108">Requirements</span></span>  
 <span data-ttu-id="2a0e4-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a0e4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a0e4-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2a0e4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a0e4-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2a0e4-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a0e4-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a0e4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0e4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a0e4-113">See Also</span></span>  
 [<span data-ttu-id="2a0e4-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2a0e4-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2a0e4-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2a0e4-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

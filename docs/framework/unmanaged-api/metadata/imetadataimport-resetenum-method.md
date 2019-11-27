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
ms.openlocfilehash: 3f965ab215ff861c6df61de82dcbbea6b389c8da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426773"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="6a51b-102">Método IMetaDataImport::ResetEnum</span><span class="sxs-lookup"><span data-stu-id="6a51b-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="6a51b-103">Redefine o enumerador especificado para a posição especificada.</span><span class="sxs-lookup"><span data-stu-id="6a51b-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a51b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a51b-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a51b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a51b-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="6a51b-106">no O enumerador a ser redefinido.</span><span class="sxs-lookup"><span data-stu-id="6a51b-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="6a51b-107">no A nova posição na qual colocar o enumerador.</span><span class="sxs-lookup"><span data-stu-id="6a51b-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a51b-108">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6a51b-108">Requirements</span></span>  
 <span data-ttu-id="6a51b-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a51b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a51b-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6a51b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a51b-111">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6a51b-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a51b-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a51b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a51b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a51b-113">See also</span></span>

- [<span data-ttu-id="6a51b-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6a51b-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6a51b-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6a51b-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

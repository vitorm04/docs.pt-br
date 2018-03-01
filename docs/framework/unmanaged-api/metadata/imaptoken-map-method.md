---
title: "Método IMapToken::Map"
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
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe034d2bc6d70e820fa3ad5de8140afa9a19a6bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="b93cf-102">Método IMapToken::Map</span><span class="sxs-lookup"><span data-stu-id="b93cf-102">IMapToken::Map Method</span></span>
<span data-ttu-id="b93cf-103">Mapeia uma relação entre os assemblies usando assinaturas de metadados.</span><span class="sxs-lookup"><span data-stu-id="b93cf-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b93cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b93cf-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b93cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b93cf-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="b93cf-106">[in] O token de metadados que representa o objeto de código importados.</span><span class="sxs-lookup"><span data-stu-id="b93cf-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="b93cf-107">[in] O token de metadados que representa o objeto de código emitido.</span><span class="sxs-lookup"><span data-stu-id="b93cf-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b93cf-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b93cf-108">Remarks</span></span>  
 <span data-ttu-id="b93cf-109">Quando o token remapear ocorre durante uma mesclagem, o token original é definido no escopo de metadados importados (origem) e o novo token tem seu escopo definido no escopo de metadados emitido (destino).</span><span class="sxs-lookup"><span data-stu-id="b93cf-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b93cf-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b93cf-110">Requirements</span></span>  
 <span data-ttu-id="b93cf-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b93cf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b93cf-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b93cf-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b93cf-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b93cf-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b93cf-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b93cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b93cf-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b93cf-115">See Also</span></span>  
 [<span data-ttu-id="b93cf-116">Interface IMapToken</span><span class="sxs-lookup"><span data-stu-id="b93cf-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)

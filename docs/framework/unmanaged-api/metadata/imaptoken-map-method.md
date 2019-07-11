---
title: Método IMapToken::Map
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ac12d5b6bc2911e3bd879285a9a12f65c426f0d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745860"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="e92a4-102">Método IMapToken::Map</span><span class="sxs-lookup"><span data-stu-id="e92a4-102">IMapToken::Map Method</span></span>
<span data-ttu-id="e92a4-103">Mapeia uma relação entre os assemblies usando assinaturas de metadados.</span><span class="sxs-lookup"><span data-stu-id="e92a4-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e92a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e92a4-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e92a4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e92a4-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="e92a4-106">[in] O token de metadados que representa o objeto de código importados.</span><span class="sxs-lookup"><span data-stu-id="e92a4-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="e92a4-107">[in] O token de metadados que representa o objeto de código emitido.</span><span class="sxs-lookup"><span data-stu-id="e92a4-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e92a4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e92a4-108">Remarks</span></span>  
 <span data-ttu-id="e92a4-109">Quando o token remapear ocorre durante uma mesclagem, o token original é definido no escopo de metadados importados (origem) e o novo token é delimitado no escopo de metadados de emitido (destino).</span><span class="sxs-lookup"><span data-stu-id="e92a4-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e92a4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e92a4-110">Requirements</span></span>  
 <span data-ttu-id="e92a4-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e92a4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e92a4-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e92a4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e92a4-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e92a4-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e92a4-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e92a4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e92a4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e92a4-115">See also</span></span>

- [<span data-ttu-id="e92a4-116">Interface IMapToken</span><span class="sxs-lookup"><span data-stu-id="e92a4-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)

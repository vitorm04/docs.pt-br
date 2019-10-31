---
title: Método ICorPublishEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
ms.openlocfilehash: a03b06143c0bd92425c7bfc13af6e374dc629f10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140481"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="bf1eb-102">Método ICorPublishEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="bf1eb-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="bf1eb-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf1eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf1eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf1eb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf1eb-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="bf1eb-106">fora Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="bf1eb-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf1eb-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf1eb-107">Requirements</span></span>  
 <span data-ttu-id="bf1eb-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf1eb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf1eb-109">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="bf1eb-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bf1eb-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf1eb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf1eb-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf1eb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf1eb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf1eb-112">See also</span></span>

- [<span data-ttu-id="bf1eb-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="bf1eb-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

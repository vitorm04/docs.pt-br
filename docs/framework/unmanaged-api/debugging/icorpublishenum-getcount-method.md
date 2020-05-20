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
ms.openlocfilehash: 7ed4236187fab1c1e81be9ddcdff1f1852e38f70
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421183"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="6b32e-102">Método ICorPublishEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="6b32e-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="6b32e-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="6b32e-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b32e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b32e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b32e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b32e-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="6b32e-106">fora Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="6b32e-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b32e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b32e-107">Requirements</span></span>  
 <span data-ttu-id="6b32e-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b32e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b32e-109">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="6b32e-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6b32e-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b32e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b32e-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b32e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b32e-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="6b32e-112">See also</span></span>

- [<span data-ttu-id="6b32e-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="6b32e-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)

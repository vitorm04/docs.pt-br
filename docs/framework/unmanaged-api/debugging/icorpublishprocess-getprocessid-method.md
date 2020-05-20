---
title: Método ICorPublishProcess::GetProcessID
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: 95a4ef3ab77b33c67c63be2c22647075f2f95ce8
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421105"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="3ef9b-102">Método ICorPublishProcess::GetProcessID</span><span class="sxs-lookup"><span data-stu-id="3ef9b-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="3ef9b-103">Obtém o identificador do sistema operacional para esse processo.</span><span class="sxs-lookup"><span data-stu-id="3ef9b-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ef9b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ef9b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ef9b-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="3ef9b-106">fora Um ponteiro para o identificador do processo representado por esse objeto [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3ef9b-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ef9b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ef9b-107">Requirements</span></span>  
 <span data-ttu-id="3ef9b-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ef9b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ef9b-109">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3ef9b-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3ef9b-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ef9b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ef9b-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ef9b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef9b-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="3ef9b-112">See also</span></span>

- [<span data-ttu-id="3ef9b-113">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="3ef9b-113">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)

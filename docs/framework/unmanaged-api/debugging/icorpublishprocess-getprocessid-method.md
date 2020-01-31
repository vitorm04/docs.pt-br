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
ms.openlocfilehash: 4cc6bbde2c7367c1109ca73e66f2670a56b2cdbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790549"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="3b607-102">Método ICorPublishProcess::GetProcessID</span><span class="sxs-lookup"><span data-stu-id="3b607-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="3b607-103">Obtém o identificador do sistema operacional para esse processo.</span><span class="sxs-lookup"><span data-stu-id="3b607-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b607-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b607-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b607-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b607-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="3b607-106">fora Um ponteiro para o identificador do processo representado por esse objeto [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3b607-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b607-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="3b607-107">Requirements</span></span>  
 <span data-ttu-id="3b607-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b607-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b607-109">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3b607-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3b607-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b607-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b607-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b607-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b607-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="3b607-112">See also</span></span>

- [<span data-ttu-id="3b607-113">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="3b607-113">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)

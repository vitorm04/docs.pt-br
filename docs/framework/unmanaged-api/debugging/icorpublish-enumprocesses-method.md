---
title: Método ICorPublish::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77bae0de732fc8847650b9ce03f8228111a76334
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466512"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="12e62-102">Método ICorPublish::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="12e62-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="12e62-103">Obtém um enumerador para os processos gerenciados em execução neste computador.</span><span class="sxs-lookup"><span data-stu-id="12e62-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e62-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12e62-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12e62-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12e62-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="12e62-106">Um valor igual a [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeração que especifica o tipo de processo a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="12e62-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="12e62-107">Na versão atual, COR_PUB_MANAGEDONLY só é válido.</span><span class="sxs-lookup"><span data-stu-id="12e62-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="12e62-108">Um ponteiro para o endereço de um [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instância que é o enumerador dos processos.</span><span class="sxs-lookup"><span data-stu-id="12e62-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12e62-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="12e62-109">Remarks</span></span>  
 <span data-ttu-id="12e62-110">Coleção do enumerador de processos se baseia em um instantâneo dos processos que estão em execução quando o `EnumProcesses` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="12e62-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="12e62-111">O enumerador não incluirá todos os processos que terminar antes ou iniciarem após `EnumProcesses` é chamado.</span><span class="sxs-lookup"><span data-stu-id="12e62-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="12e62-112">O `EnumProcesses` método pode ser chamado mais de uma vez neste [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instância para criar uma nova coleção atualizada de processos.</span><span class="sxs-lookup"><span data-stu-id="12e62-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="12e62-113">Coleções existentes não serão afetadas por chamadas subsequentes do `EnumProcesses` método.</span><span class="sxs-lookup"><span data-stu-id="12e62-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12e62-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12e62-114">Requirements</span></span>  
 <span data-ttu-id="12e62-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12e62-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12e62-116">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="12e62-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="12e62-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12e62-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12e62-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12e62-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e62-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12e62-119">See also</span></span>
- [<span data-ttu-id="12e62-120">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="12e62-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

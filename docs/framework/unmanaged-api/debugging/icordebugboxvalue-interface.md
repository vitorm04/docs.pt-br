---
title: Interface ICorDebugBoxValue
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
ms.openlocfilehash: bece1be7474c57d38f083e322c2af1b0ba705ee9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894761"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="ad7a0-102">Interface ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="ad7a0-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="ad7a0-103">Uma subclasse de "ICorDebugHeapValue" que representa um objeto de classe de valor em caixa.</span><span class="sxs-lookup"><span data-stu-id="ad7a0-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad7a0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ad7a0-104">Methods</span></span>  
  
|<span data-ttu-id="ad7a0-105">Método</span><span class="sxs-lookup"><span data-stu-id="ad7a0-105">Method</span></span>|<span data-ttu-id="ad7a0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad7a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad7a0-107">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="ad7a0-107">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="ad7a0-108">Obtém um ponteiro de interface para a instância "ICorDebugObjectValue" do box.</span><span class="sxs-lookup"><span data-stu-id="ad7a0-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad7a0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad7a0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad7a0-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="ad7a0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad7a0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad7a0-111">Requirements</span></span>  
 <span data-ttu-id="ad7a0-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad7a0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad7a0-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad7a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad7a0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad7a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad7a0-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad7a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7a0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad7a0-116">See also</span></span>

- [<span data-ttu-id="ad7a0-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ad7a0-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

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
ms.openlocfilehash: 1ec54f4fe36aaf38d7c0ce0586733729bd2fddea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784463"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="1d140-102">Interface ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="1d140-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="1d140-103">Uma subclasse de "ICorDebugHeapValue" que representa um objeto de classe de valor em caixa.</span><span class="sxs-lookup"><span data-stu-id="1d140-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d140-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1d140-104">Methods</span></span>  
  
|<span data-ttu-id="1d140-105">Método</span><span class="sxs-lookup"><span data-stu-id="1d140-105">Method</span></span>|<span data-ttu-id="1d140-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d140-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d140-107">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="1d140-107">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="1d140-108">Obtém um ponteiro de interface para a instância "ICorDebugObjectValue" do box.</span><span class="sxs-lookup"><span data-stu-id="1d140-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d140-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d140-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d140-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="1d140-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d140-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="1d140-111">Requirements</span></span>  
 <span data-ttu-id="1d140-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d140-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d140-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d140-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d140-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d140-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d140-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d140-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d140-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="1d140-116">See also</span></span>

- [<span data-ttu-id="1d140-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1d140-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

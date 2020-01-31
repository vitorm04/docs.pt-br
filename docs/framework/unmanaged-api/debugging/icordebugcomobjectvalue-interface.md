---
title: Interface ICorDebugComObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: ed5b39ed4b2a14c071bf23fb04efbad6834e8a9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783968"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="27240-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="27240-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="27240-103">Fornece métodos para recuperar informações associadas a um RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="27240-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27240-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="27240-104">Methods</span></span>  
  
|<span data-ttu-id="27240-105">Método</span><span class="sxs-lookup"><span data-stu-id="27240-105">Method</span></span>|<span data-ttu-id="27240-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="27240-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27240-107">Método GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="27240-107">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="27240-108">Obtém os ponteiros de interface bruto armazenados em cache no RCW atual.</span><span class="sxs-lookup"><span data-stu-id="27240-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="27240-109">Método GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="27240-109">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="27240-110">Fornece um enumerador para os tipos de interface para os quais o objeto atual foi usado em maiúsculas ou usados.</span><span class="sxs-lookup"><span data-stu-id="27240-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27240-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="27240-111">Remarks</span></span>  
 <span data-ttu-id="27240-112">Para verificar se uma instância de uma interface "ICorDebugValue" representa um RCW, um depurador chama `QueryInterface` em "ICorDebugValue" com `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="27240-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27240-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="27240-113">Requirements</span></span>  
 <span data-ttu-id="27240-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27240-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27240-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27240-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27240-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27240-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27240-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27240-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27240-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="27240-118">See also</span></span>

- [<span data-ttu-id="27240-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="27240-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="27240-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="27240-120">Debugging</span></span>](index.md)

---
title: Método ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 0c67f8bdce49b4e9200b501aaf00ae293cced7d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783410"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="14e02-102">Método ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="14e02-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="14e02-103">Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.</span><span class="sxs-lookup"><span data-stu-id="14e02-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14e02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14e02-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14e02-105">Parameters</span></span>  
 <span data-ttu-id="14e02-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="14e02-106">pDebugEventKind</span></span>  
 <span data-ttu-id="14e02-107">Um ponteiro para um membro de enumeração [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) que indica o tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="14e02-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14e02-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="14e02-108">Remarks</span></span>  
 <span data-ttu-id="14e02-109">Com base no valor de `pDebugEventKind`, você pode chamar `QueryInterface` para obter uma interface de evento de depuração mais precisa com dados adicionais.</span><span class="sxs-lookup"><span data-stu-id="14e02-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14e02-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14e02-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14e02-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="14e02-111">Requirements</span></span>  
 <span data-ttu-id="14e02-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14e02-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14e02-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14e02-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14e02-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14e02-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14e02-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14e02-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e02-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="14e02-116">See also</span></span>

- [<span data-ttu-id="14e02-117">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="14e02-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="14e02-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="14e02-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

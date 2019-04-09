---
title: Método ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62eede48eea01563dbc3e170720694a24343d0a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150521"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="589cf-102">Método ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="589cf-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="589cf-103">Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.</span><span class="sxs-lookup"><span data-stu-id="589cf-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="589cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="589cf-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="589cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="589cf-105">Parameters</span></span>  
 <span data-ttu-id="589cf-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="589cf-106">pDebugEventKind</span></span>  
 <span data-ttu-id="589cf-107">Um ponteiro para um [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) membro de enumeração que indica o tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="589cf-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="589cf-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="589cf-108">Remarks</span></span>  
 <span data-ttu-id="589cf-109">Com base no valor de `pDebugEventKind`, você pode chamar `QueryInterface` para obter uma interface de evento de depuração mais precisa com dados adicionais.</span><span class="sxs-lookup"><span data-stu-id="589cf-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="589cf-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="589cf-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="589cf-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="589cf-111">Requirements</span></span>  
 <span data-ttu-id="589cf-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="589cf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="589cf-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="589cf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="589cf-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="589cf-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="589cf-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="589cf-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="589cf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="589cf-116">See also</span></span>

- [<span data-ttu-id="589cf-117">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="589cf-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="589cf-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="589cf-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

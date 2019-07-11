---
title: Enumeração CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059e823110686a2b939c9664fa5b67e4041c3486
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740317"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="faaa4-102">Enumeração CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="faaa4-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="faaa4-103">Descreve como uma função exportada invocará o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="faaa4-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faaa4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faaa4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="faaa4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="faaa4-105">Members</span></span>  
  
|<span data-ttu-id="faaa4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="faaa4-106">Member</span></span>|<span data-ttu-id="faaa4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="faaa4-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="faaa4-108">Se algum código gerenciado for invocado por este método, precisará ser localizadas por eventos explícitos ou pontos de interrupção posteriormente.</span><span class="sxs-lookup"><span data-stu-id="faaa4-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="faaa4-109">--ou--</span><span class="sxs-lookup"><span data-stu-id="faaa4-109">--or--</span></span><br /><br /> <span data-ttu-id="faaa4-110">Podemos perder parte do código gerenciado que este método chama porque não há nenhuma maneira fácil de pará-lo.</span><span class="sxs-lookup"><span data-stu-id="faaa4-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="faaa4-111">--ou--</span><span class="sxs-lookup"><span data-stu-id="faaa4-111">--or--</span></span><br /><br /> <span data-ttu-id="faaa4-112">O método nunca pode invocar um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="faaa4-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="faaa4-113">Esse método invocará o código gerenciado por meio de uma instrução de retorno.</span><span class="sxs-lookup"><span data-stu-id="faaa4-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="faaa4-114">Sair deve dar no próximo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="faaa4-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="faaa4-115">Esse método invocará o código gerenciado por meio de chamada tail.</span><span class="sxs-lookup"><span data-stu-id="faaa4-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="faaa4-116">Seguir uma etapa única e ignorar quaisquer instruções de chamada devem dar no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="faaa4-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faaa4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="faaa4-117">Remarks</span></span>  
 <span data-ttu-id="faaa4-118">Essa enumeração é usada pelo [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) método para fornecer informações sobre como percorrer o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="faaa4-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="faaa4-119">Essa enumeração destina-se para uso no .NET Native somente para cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="faaa4-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faaa4-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="faaa4-120">Requirements</span></span>  
 <span data-ttu-id="faaa4-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faaa4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faaa4-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="faaa4-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="faaa4-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faaa4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faaa4-124">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faaa4-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faaa4-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faaa4-125">See also</span></span>

- [<span data-ttu-id="faaa4-126">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="faaa4-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="faaa4-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="faaa4-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

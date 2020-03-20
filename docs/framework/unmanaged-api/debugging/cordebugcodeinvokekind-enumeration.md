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
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179255"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="39cc5-102">Enumeração CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="39cc5-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="39cc5-103">Descreve como uma função exportada invoca código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="39cc5-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39cc5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39cc5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,
    CODE_INVOKE_KIND_RETURN,
    CODE_INVOKE_KIND_TAILCALL,
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="39cc5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="39cc5-105">Members</span></span>  
  
|<span data-ttu-id="39cc5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="39cc5-106">Member</span></span>|<span data-ttu-id="39cc5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="39cc5-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="39cc5-108">Se algum código gerenciado for invocado por este método, precisará ser localizadas por eventos explícitos ou pontos de interrupção posteriormente.</span><span class="sxs-lookup"><span data-stu-id="39cc5-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="39cc5-109">--ou--</span><span class="sxs-lookup"><span data-stu-id="39cc5-109">--or--</span></span><br /><br /> <span data-ttu-id="39cc5-110">Podemos perder parte do código gerenciado que este método chama porque não há nenhuma maneira fácil de pará-lo.</span><span class="sxs-lookup"><span data-stu-id="39cc5-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="39cc5-111">--ou--</span><span class="sxs-lookup"><span data-stu-id="39cc5-111">--or--</span></span><br /><br /> <span data-ttu-id="39cc5-112">O método nunca pode invocar um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="39cc5-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="39cc5-113">Esse método invocará o código gerenciado por meio de uma instrução de retorno.</span><span class="sxs-lookup"><span data-stu-id="39cc5-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="39cc5-114">Sair deve dar no próximo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="39cc5-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="39cc5-115">Esse método invocará o código gerenciado por meio de chamada tail.</span><span class="sxs-lookup"><span data-stu-id="39cc5-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="39cc5-116">Seguir uma etapa única e ignorar quaisquer instruções de chamada devem dar no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="39cc5-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39cc5-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="39cc5-117">Remarks</span></span>  
 <span data-ttu-id="39cc5-118">Essa enumeração é usada pelo método [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) para fornecer informações sobre a revisão do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="39cc5-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39cc5-119">Esta enumeração destina-se a ser usada apenas em cenários de depuração nativos .NET.</span><span class="sxs-lookup"><span data-stu-id="39cc5-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39cc5-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39cc5-120">Requirements</span></span>  
 <span data-ttu-id="39cc5-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39cc5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39cc5-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39cc5-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39cc5-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39cc5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39cc5-124">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39cc5-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39cc5-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="39cc5-125">See also</span></span>

- [<span data-ttu-id="39cc5-126">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="39cc5-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="39cc5-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="39cc5-127">Debugging</span></span>](index.md)

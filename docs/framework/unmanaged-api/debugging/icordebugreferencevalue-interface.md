---
title: Interface ICorDebugReferenceValue
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 2efba22b4ec372c5ddedd4982a29d66945d3511c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792128"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="8df21-102">Interface ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="8df21-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="8df21-103">Fornece métodos que gerenciam um valor que é uma referência a um objeto.</span><span class="sxs-lookup"><span data-stu-id="8df21-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="8df21-104">(Ou seja, essa interface fornece métodos que gerenciam um ponteiro.) Essa interface implementa "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="8df21-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8df21-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8df21-105">Methods</span></span>  
  
|<span data-ttu-id="8df21-106">Método</span><span class="sxs-lookup"><span data-stu-id="8df21-106">Method</span></span>|<span data-ttu-id="8df21-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8df21-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8df21-108">Método Dereference</span><span class="sxs-lookup"><span data-stu-id="8df21-108">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="8df21-109">Obtém o objeto que é referenciado.</span><span class="sxs-lookup"><span data-stu-id="8df21-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="8df21-110">Método DereferenceStrong</span><span class="sxs-lookup"><span data-stu-id="8df21-110">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="8df21-111">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="8df21-111">Not implemented.</span></span> <span data-ttu-id="8df21-112">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="8df21-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="8df21-113">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="8df21-113">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="8df21-114">Obtém o endereço de memória atual do objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="8df21-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="8df21-115">Método IsNull</span><span class="sxs-lookup"><span data-stu-id="8df21-115">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="8df21-116">Obtém um valor que indica se este `ICorDebugReferenceValue` é um valor nulo; nesse caso, o `ICorDebugReferenceValue` não aponta para um objeto.</span><span class="sxs-lookup"><span data-stu-id="8df21-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="8df21-117">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="8df21-117">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="8df21-118">Define o endereço de memória atual.</span><span class="sxs-lookup"><span data-stu-id="8df21-118">Sets the current memory address.</span></span> <span data-ttu-id="8df21-119">Ou seja, esse método define esse `ICorDebugReferenceValue` para apontar para um objeto.</span><span class="sxs-lookup"><span data-stu-id="8df21-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8df21-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="8df21-120">Remarks</span></span>  
 <span data-ttu-id="8df21-121">O Common Language Runtime (CLR) pode fazer uma coleta de lixo em objetos quando o processo depurado é continuado.</span><span class="sxs-lookup"><span data-stu-id="8df21-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="8df21-122">A coleta de lixo pode mover objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="8df21-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="8df21-123">Um `ICorDebugReferenceValue` irá cooperar com a coleta de lixo para que suas informações sejam atualizadas após a coleta de lixo, ou elas serão invalidadas implicitamente antes da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8df21-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="8df21-124">O objeto `ICorDebugReferenceValue` pode ser implicitamente invalidado depois que o processo depurado tiver sido continuado.</span><span class="sxs-lookup"><span data-stu-id="8df21-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="8df21-125">O "ICorDebugHandleValue" derivado não será invalidado até ser liberado ou exposto explicitamente.</span><span class="sxs-lookup"><span data-stu-id="8df21-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8df21-126">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="8df21-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8df21-127">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="8df21-127">Requirements</span></span>  
 <span data-ttu-id="8df21-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8df21-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8df21-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8df21-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8df21-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8df21-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8df21-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8df21-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df21-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="8df21-132">See also</span></span>

- [<span data-ttu-id="8df21-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8df21-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

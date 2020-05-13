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
ms.openlocfilehash: 6c6ff428e378e973d8846674ffacdcd04b2dbdbc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378345"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="fd524-102">Interface ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="fd524-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="fd524-103">Fornece métodos que gerenciam um valor que é uma referência a um objeto.</span><span class="sxs-lookup"><span data-stu-id="fd524-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="fd524-104">(Ou seja, essa interface fornece métodos que gerenciam um ponteiro.) Essa interface implementa "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="fd524-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd524-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="fd524-105">Methods</span></span>  
  
|<span data-ttu-id="fd524-106">Método</span><span class="sxs-lookup"><span data-stu-id="fd524-106">Method</span></span>|<span data-ttu-id="fd524-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd524-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd524-108">Método Dereference</span><span class="sxs-lookup"><span data-stu-id="fd524-108">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="fd524-109">Obtém o objeto que é referenciado.</span><span class="sxs-lookup"><span data-stu-id="fd524-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="fd524-110">Método DereferenceStrong</span><span class="sxs-lookup"><span data-stu-id="fd524-110">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="fd524-111">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="fd524-111">Not implemented.</span></span> <span data-ttu-id="fd524-112">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="fd524-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="fd524-113">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="fd524-113">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="fd524-114">Obtém o endereço de memória atual do objeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="fd524-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="fd524-115">Método IsNull</span><span class="sxs-lookup"><span data-stu-id="fd524-115">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="fd524-116">Obtém um valor que indica se este `ICorDebugReferenceValue` é um valor nulo; nesse caso, o `ICorDebugReferenceValue` não aponta para um objeto.</span><span class="sxs-lookup"><span data-stu-id="fd524-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="fd524-117">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="fd524-117">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="fd524-118">Define o endereço de memória atual.</span><span class="sxs-lookup"><span data-stu-id="fd524-118">Sets the current memory address.</span></span> <span data-ttu-id="fd524-119">Ou seja, esse método define isso `ICorDebugReferenceValue` para apontar para um objeto.</span><span class="sxs-lookup"><span data-stu-id="fd524-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd524-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd524-120">Remarks</span></span>  
 <span data-ttu-id="fd524-121">O Common Language Runtime (CLR) pode fazer uma coleta de lixo em objetos quando o processo depurado é continuado.</span><span class="sxs-lookup"><span data-stu-id="fd524-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="fd524-122">A coleta de lixo pode mover objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="fd524-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="fd524-123">Um `ICorDebugReferenceValue` irá cooperar com a coleta de lixo para que suas informações sejam atualizadas após a coleta de lixo, ou elas serão invalidadas implicitamente antes da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="fd524-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="fd524-124">O `ICorDebugReferenceValue` objeto pode ser implicitamente invalidado depois que o processo depurado tiver sido continuado.</span><span class="sxs-lookup"><span data-stu-id="fd524-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="fd524-125">O "ICorDebugHandleValue" derivado não será invalidado até ser liberado ou exposto explicitamente.</span><span class="sxs-lookup"><span data-stu-id="fd524-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd524-126">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="fd524-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd524-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd524-127">Requirements</span></span>  
 <span data-ttu-id="fd524-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd524-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd524-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd524-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd524-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd524-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd524-131">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd524-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd524-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd524-132">See also</span></span>

- [<span data-ttu-id="fd524-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fd524-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

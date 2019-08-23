---
title: Interface ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d180d57431e34d872ff077e6bc597175029688e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962713"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="82642-102">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="82642-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="82642-103">Estende logicamente a interface ICorDebugProcess para habilitar recursos como decodificação de eventos de depuração gerenciados que são codificados em eventos de depuração de exceção nativa e divisão de módulo virtual.</span><span class="sxs-lookup"><span data-stu-id="82642-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82642-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="82642-104">Methods</span></span>  
  
|<span data-ttu-id="82642-105">Método</span><span class="sxs-lookup"><span data-stu-id="82642-105">Method</span></span>|<span data-ttu-id="82642-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="82642-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82642-107">Método DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="82642-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="82642-108">Decodifica eventos de depuração gerenciados que foram encapsulados na carga de eventos de depuração de exceção nativo especialmente criado.</span><span class="sxs-lookup"><span data-stu-id="82642-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="82642-109">Método EnableVirtualModuleSplitting</span><span class="sxs-lookup"><span data-stu-id="82642-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="82642-110">Habilita ou desabilita a divisão de módulo virtual.</span><span class="sxs-lookup"><span data-stu-id="82642-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="82642-111">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="82642-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="82642-112">Obtém informações sobre o código gerenciado em um endereço de código em particular.</span><span class="sxs-lookup"><span data-stu-id="82642-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="82642-113">Método GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="82642-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="82642-114">Fornece informações sobre funções exportadas de tempo de execução para ajudar a percorrer o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="82642-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="82642-115">Método MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="82642-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="82642-116">Altera o estado interno do depurado para que o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> na biblioteca de classes .NET Framework retorne `true`.</span><span class="sxs-lookup"><span data-stu-id="82642-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="82642-117">Método ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="82642-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="82642-118">Notifica o [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) de que o processo está em execução.</span><span class="sxs-lookup"><span data-stu-id="82642-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82642-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="82642-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82642-120">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="82642-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="82642-121">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface `E_NOINTERFACE` retorna para cenários ICorDebug fora do .net Native.</span><span class="sxs-lookup"><span data-stu-id="82642-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82642-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82642-122">Requirements</span></span>  
 <span data-ttu-id="82642-123">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82642-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82642-124">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82642-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82642-125">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82642-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82642-126">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82642-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82642-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82642-127">See also</span></span>

- [<span data-ttu-id="82642-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="82642-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="82642-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="82642-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

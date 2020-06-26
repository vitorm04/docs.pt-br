---
title: MDA exceptionSwallowedOnCallFromCom
description: Examine o assistente de depuração gerenciada do exceptionSwallowedOnCallFromCOM no .NET. Esse MDA ocorre se uma exceção foi lançada, mas não há uma boa maneira de relatá-la.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 434f06cf953147d5c245e625db997bed6dbef700
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415947"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="7fd77-104">MDA exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="7fd77-104">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="7fd77-105">O `exceptionSwallowedOnCallFromCOM` MDA (assistente para depuração gerenciada) é ativado quando uma exceção é lançada do código do CLR (Common Language Runtime) chamado do COM por meio de um método que não tem um tipo de retorno HRESULT não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="7fd77-105">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7fd77-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="7fd77-106">Symptoms</span></span>  
 <span data-ttu-id="7fd77-107">Uma chamada para um componente gerenciado de COM retorna um valor de FALSE ou 0.</span><span class="sxs-lookup"><span data-stu-id="7fd77-107">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="7fd77-108">Como alternativa, se o método tiver um tipo de retorno nulo, pode não haver indicação de que foi lançada uma exceção durante a execução do método.</span><span class="sxs-lookup"><span data-stu-id="7fd77-108">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="7fd77-109">Nesse caso, a exceção será capturada silenciosamente e a execução retornará ao chamador do COM.</span><span class="sxs-lookup"><span data-stu-id="7fd77-109">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7fd77-110">Causa</span><span class="sxs-lookup"><span data-stu-id="7fd77-110">Cause</span></span>  
 <span data-ttu-id="7fd77-111">Uma exceção foi lançada, mas não há uma maneira válida de relatá-la.</span><span class="sxs-lookup"><span data-stu-id="7fd77-111">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7fd77-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="7fd77-112">Resolution</span></span>  
 <span data-ttu-id="7fd77-113">Somente informativo, não indica necessariamente um bug.</span><span class="sxs-lookup"><span data-stu-id="7fd77-113">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7fd77-114">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="7fd77-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="7fd77-115">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="7fd77-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="7fd77-116">Ele apenas relata dados sobre exceções capturadas silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="7fd77-116">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7fd77-117">Saída</span><span class="sxs-lookup"><span data-stu-id="7fd77-117">Output</span></span>  
 <span data-ttu-id="7fd77-118">Mensagem informativa contendo o nome do método, o nome do tipo e a mensagem de exceção.</span><span class="sxs-lookup"><span data-stu-id="7fd77-118">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7fd77-119">Configuração</span><span class="sxs-lookup"><span data-stu-id="7fd77-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fd77-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="7fd77-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7fd77-121">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="7fd77-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7fd77-122">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="7fd77-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)

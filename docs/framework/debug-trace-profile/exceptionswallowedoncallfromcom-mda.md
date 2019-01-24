---
title: MDA exceptionSwallowedOnCallFromCom
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aebcd2d2f2387f478c36e84dad82d90d4d70d68e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554667"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="efb25-102">MDA exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="efb25-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="efb25-103">O `exceptionSwallowedOnCallFromCOM` MDA (assistente para depuração gerenciada) é ativado quando uma exceção é lançada do código do CLR (Common Language Runtime) chamado do COM por meio de um método que não tem um tipo de retorno HRESULT não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="efb25-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="efb25-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="efb25-104">Symptoms</span></span>  
 <span data-ttu-id="efb25-105">Uma chamada para um componente gerenciado de COM retorna um valor de FALSE ou 0.</span><span class="sxs-lookup"><span data-stu-id="efb25-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="efb25-106">Como alternativa, se o método tiver um tipo de retorno nulo, pode não haver indicação de que foi lançada uma exceção durante a execução do método.</span><span class="sxs-lookup"><span data-stu-id="efb25-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="efb25-107">Nesse caso, a exceção será capturada silenciosamente e a execução retornará ao chamador do COM.</span><span class="sxs-lookup"><span data-stu-id="efb25-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="efb25-108">Causa</span><span class="sxs-lookup"><span data-stu-id="efb25-108">Cause</span></span>  
 <span data-ttu-id="efb25-109">Uma exceção foi lançada, mas não há uma maneira válida de relatá-la.</span><span class="sxs-lookup"><span data-stu-id="efb25-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="efb25-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="efb25-110">Resolution</span></span>  
 <span data-ttu-id="efb25-111">Somente informativo, não indica necessariamente um bug.</span><span class="sxs-lookup"><span data-stu-id="efb25-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="efb25-112">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="efb25-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="efb25-113">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="efb25-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="efb25-114">Ele apenas relata dados sobre exceções capturadas silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="efb25-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="efb25-115">Saída</span><span class="sxs-lookup"><span data-stu-id="efb25-115">Output</span></span>  
 <span data-ttu-id="efb25-116">Mensagem informativa contendo o nome do método, o nome do tipo e a mensagem de exceção.</span><span class="sxs-lookup"><span data-stu-id="efb25-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="efb25-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="efb25-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="efb25-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="efb25-118">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="efb25-119">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="efb25-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="efb25-120">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="efb25-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

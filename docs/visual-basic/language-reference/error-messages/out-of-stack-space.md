---
title: "Sem espaço na pilha (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="60266-102">Sem espaço na pilha (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60266-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="60266-103">A pilha é uma área de trabalho de memória aumenta e diminui dinamicamente com as demandas do seu programa em execução.</span><span class="sxs-lookup"><span data-stu-id="60266-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="60266-104">Os limites foram excedidos.</span><span class="sxs-lookup"><span data-stu-id="60266-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60266-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="60266-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="60266-106">Verifique se os procedimentos não estão aninhados muito profundamente.</span><span class="sxs-lookup"><span data-stu-id="60266-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="60266-107">Certifique-se de procedimentos recursivos encerrar corretamente.</span><span class="sxs-lookup"><span data-stu-id="60266-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="60266-108">Se as variáveis locais exigem mais espaço de variável local que está disponível, tente declarando algumas variáveis no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="60266-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="60266-109">Também é possível declarar todas as variáveis no procedimento estático precedendo o `Property`, `Sub`, ou `Function` a palavra-chave `Static`.</span><span class="sxs-lookup"><span data-stu-id="60266-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="60266-110">Ou você pode usar o `Static` instrução para declarar variáveis estáticas individuais dentro de procedimentos.</span><span class="sxs-lookup"><span data-stu-id="60266-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="60266-111">Redefina algumas das suas cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, como cadeias de caracteres de comprimento fixo usam mais espaço de pilha que cadeias de caracteres de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="60266-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="60266-112">Você também pode definir a cadeia de caracteres no nível de módulo em que ele requer que nenhum espaço de pilha.</span><span class="sxs-lookup"><span data-stu-id="60266-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="60266-113">Verifique o número de aninhada `DoEvents` chamadas de função, usando o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="60266-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="60266-114">Certifique-se de que não causava uma cascata"evento" Disparando um evento que chama um procedimento de evento já na pilha.</span><span class="sxs-lookup"><span data-stu-id="60266-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="60266-115">Cascata de eventos é semelhante a uma chamada de procedimento não finalizada recursiva, mas é menos óbvio, desde que a chamada é feita por [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] em vez de uma chamada explícita no código.</span><span class="sxs-lookup"><span data-stu-id="60266-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="60266-116">Use o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="60266-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60266-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60266-117">See Also</span></span>  
 [<span data-ttu-id="60266-118">Janelas de Memória</span><span class="sxs-lookup"><span data-stu-id="60266-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)

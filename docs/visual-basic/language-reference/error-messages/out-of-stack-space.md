---
title: "(Visual Basic) de espaço de pilha | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
dev_langs:
- VB
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 256ef0c7fcb3632e0c13d12737d438225343884f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="6a6c4-102">Sem espaço na pilha (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a6c4-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="6a6c4-103">A pilha é uma área de trabalho de memória aumenta e diminui dinamicamente com as demandas do seu programa em execução.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="6a6c4-104">Os limites foram excedidos.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a6c4-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6a6c4-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="6a6c4-106">Verifique se os procedimentos não estão aninhados muito profundamente.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="6a6c4-107">Certifique-se de procedimentos recursivos encerrar corretamente.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="6a6c4-108">Se as variáveis locais exigem mais espaço de variável local que está disponível, tente declarar algumas variáveis no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="6a6c4-109">Você também pode declarar todas as variáveis no procedimento estático precedendo o `Property`, `Sub`, ou `Function` a palavra-chave `Static`.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="6a6c4-110">Ou você pode usar o `Static` instrução Declare variáveis estáticas individuais dentro de procedimentos.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="6a6c4-111">Redefina algumas das suas cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, como cadeias de caracteres de comprimento fixo usam mais espaço de pilha que cadeias de caracteres de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="6a6c4-112">Você também pode definir a cadeia de caracteres no nível de módulo em que ele requer que nenhum espaço de pilha.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="6a6c4-113">Verifique o número de aninhada `DoEvents` chamadas de função, usando o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="6a6c4-114">Certificar-se de que você não causa uma cascata"eventos" Disparando um evento que chama um procedimento de evento já na pilha.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="6a6c4-115">Cascata de eventos é semelhante a uma chamada de procedimento não finalizada recursiva, mas é menos óbvio, desde que a chamada é feita por [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] em vez de uma chamada explícita no código.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="6a6c4-116">Use o `Calls`caixa de diálogo exibe quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="6a6c4-116">Use the `Calls`dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6c4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a6c4-117">See Also</span></span>  
 [<span data-ttu-id="6a6c4-118">Janelas de Memória</span><span class="sxs-lookup"><span data-stu-id="6a6c4-118">Memory Windows</span></span>](https://docs.microsoft.com/visualstudio/debugger/memory-windows)

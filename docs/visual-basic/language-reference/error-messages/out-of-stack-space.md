---
title: Espaço em pilha insuficiente
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: afb6a42372bdbd2e49ac15fbbf2b9e254f8db431
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871317"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="a3294-102">Sem espaço na pilha (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3294-102">Out of stack space (Visual Basic)</span></span>

<span data-ttu-id="a3294-103">A pilha é uma área de trabalho de memória que aumenta e diminui dinamicamente com as demandas de seu programa em execução.</span><span class="sxs-lookup"><span data-stu-id="a3294-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="a3294-104">Seus limites foram excedidos.</span><span class="sxs-lookup"><span data-stu-id="a3294-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a3294-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a3294-105">To correct this error</span></span>  
  
1. <span data-ttu-id="a3294-106">Verifique se os procedimentos não estão aninhados muito profundamente.</span><span class="sxs-lookup"><span data-stu-id="a3294-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="a3294-107">Certifique-se de que os procedimentos recursivos sejam encerrados corretamente.</span><span class="sxs-lookup"><span data-stu-id="a3294-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="a3294-108">Se variáveis locais exigirem mais espaço de variável local do que o disponível, tente declarar algumas variáveis no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="a3294-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="a3294-109">Você também pode declarar todas as variáveis no procedimento estático precedendo `Property` a `Sub` `Function` palavra-chave, ou com `Static` .</span><span class="sxs-lookup"><span data-stu-id="a3294-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="a3294-110">Ou você pode usar a `Static` instrução para declarar variáveis estáticas individuais dentro de procedimentos.</span><span class="sxs-lookup"><span data-stu-id="a3294-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="a3294-111">Redefina algumas das cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, pois as cadeias de caracteres de comprimento fixo usam mais espaço de pilha que as cadeias de caracteres de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="a3294-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="a3294-112">Você também pode definir a cadeia de caracteres no nível do módulo, em que ele não requer espaço de pilha.</span><span class="sxs-lookup"><span data-stu-id="a3294-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="a3294-113">Verifique o número de chamadas de função aninhadas `DoEvents` , usando a `Calls` caixa de diálogo para exibir quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="a3294-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="a3294-114">Verifique se você não causou uma "cascata de eventos" disparando um evento que chama um procedimento de evento já na pilha.</span><span class="sxs-lookup"><span data-stu-id="a3294-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="a3294-115">Uma cascata de eventos é semelhante a uma chamada de procedimento Recursivo não finalizada, mas é menos óbvia, já que a chamada é feita por Visual Basic em vez de uma chamada explícita no código.</span><span class="sxs-lookup"><span data-stu-id="a3294-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="a3294-116">Use a `Calls` caixa de diálogo para exibir quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="a3294-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3294-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="a3294-117">See also</span></span>

- [<span data-ttu-id="a3294-118">Janelas de memória</span><span class="sxs-lookup"><span data-stu-id="a3294-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)

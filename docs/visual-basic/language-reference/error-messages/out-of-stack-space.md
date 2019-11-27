---
title: Espaço em pilha insuficiente
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349190"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="1676d-102">Sem espaço na pilha (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1676d-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="1676d-103">A pilha é uma área de trabalho de memória que aumenta e diminui dinamicamente com as demandas de seu programa em execução.</span><span class="sxs-lookup"><span data-stu-id="1676d-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="1676d-104">Seus limites foram excedidos.</span><span class="sxs-lookup"><span data-stu-id="1676d-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1676d-105">Para corrigir esse erro</span><span class="sxs-lookup"><span data-stu-id="1676d-105">To correct this error</span></span>  
  
1. <span data-ttu-id="1676d-106">Verifique se os procedimentos não estão aninhados muito profundamente.</span><span class="sxs-lookup"><span data-stu-id="1676d-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="1676d-107">Certifique-se de que os procedimentos recursivos sejam encerrados corretamente.</span><span class="sxs-lookup"><span data-stu-id="1676d-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="1676d-108">Se variáveis locais exigirem mais espaço de variável local do que o disponível, tente declarar algumas variáveis no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="1676d-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="1676d-109">Você também pode declarar todas as variáveis no procedimento estático, precedendo a palavra-chave `Property`, `Sub`ou `Function` com `Static`.</span><span class="sxs-lookup"><span data-stu-id="1676d-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="1676d-110">Ou você pode usar a instrução `Static` para declarar variáveis estáticas individuais dentro de procedimentos.</span><span class="sxs-lookup"><span data-stu-id="1676d-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="1676d-111">Redefina algumas das cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, pois as cadeias de caracteres de comprimento fixo usam mais espaço de pilha que as cadeias de caracteres de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="1676d-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="1676d-112">Você também pode definir a cadeia de caracteres no nível do módulo, em que ele não requer espaço de pilha.</span><span class="sxs-lookup"><span data-stu-id="1676d-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="1676d-113">Verifique o número de chamadas de função `DoEvents` aninhadas, usando a caixa de diálogo `Calls` para exibir quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="1676d-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="1676d-114">Verifique se você não causou uma "cascata de eventos" disparando um evento que chama um procedimento de evento já na pilha.</span><span class="sxs-lookup"><span data-stu-id="1676d-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="1676d-115">Uma cascata de eventos é semelhante a uma chamada de procedimento Recursivo não finalizada, mas é menos óbvia, já que a chamada é feita por Visual Basic em vez de uma chamada explícita no código.</span><span class="sxs-lookup"><span data-stu-id="1676d-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="1676d-116">Use a caixa de diálogo `Calls` para exibir quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="1676d-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1676d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1676d-117">See also</span></span>

- [<span data-ttu-id="1676d-118">Janelas de Memória</span><span class="sxs-lookup"><span data-stu-id="1676d-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)

---
title: Sem espaço na pilha (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 29dbdf74808fc98bb856483c3fd8e3a09a72113b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925574"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="3e507-102">Sem espaço na pilha (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e507-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="3e507-103">A pilha é uma área de trabalho de memória que aumenta e diminui dinamicamente com as demandas do seu programa em execução.</span><span class="sxs-lookup"><span data-stu-id="3e507-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="3e507-104">Seus limites forem excedidos.</span><span class="sxs-lookup"><span data-stu-id="3e507-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3e507-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3e507-105">To correct this error</span></span>  
  
1. <span data-ttu-id="3e507-106">Verifique se os procedimentos não estão aninhados muito profundamente.</span><span class="sxs-lookup"><span data-stu-id="3e507-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="3e507-107">Certifique-se de procedimentos recursivos encerrar corretamente.</span><span class="sxs-lookup"><span data-stu-id="3e507-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="3e507-108">Se as variáveis locais exigem mais espaço de variável local que está disponível, tente declarar algumas variáveis no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="3e507-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="3e507-109">Você também pode declarar todas as variáveis no procedimento estático, precedendo o `Property`, `Sub`, ou `Function` palavra-chave with `Static`.</span><span class="sxs-lookup"><span data-stu-id="3e507-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="3e507-110">Ou você pode usar o `Static` declaração para declarar variáveis estáticas individuais dentro de procedimentos.</span><span class="sxs-lookup"><span data-stu-id="3e507-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="3e507-111">Redefina algumas das suas cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, como cadeias de caracteres de comprimento fixo usam mais espaço de pilha que cadeias de caracteres de comprimento variável.</span><span class="sxs-lookup"><span data-stu-id="3e507-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="3e507-112">Você também pode definir a cadeia de caracteres no nível de módulo em que ele requer que nenhum espaço de pilha.</span><span class="sxs-lookup"><span data-stu-id="3e507-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="3e507-113">Verifique o número de aninhados `DoEvents` chamadas de função, usando o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="3e507-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="3e507-114">Verifique se que você não causou uma cascata"eventos" Disparando um evento que chama um procedimento de evento já na pilha.</span><span class="sxs-lookup"><span data-stu-id="3e507-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="3e507-115">Cascata de eventos é semelhante a uma chamada de procedimento recursivo não terminado, mas é menos óbvio, já que a chamada é feita pelo Visual Basic, em vez de uma chamada explícita no código.</span><span class="sxs-lookup"><span data-stu-id="3e507-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="3e507-116">Use o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.</span><span class="sxs-lookup"><span data-stu-id="3e507-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e507-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e507-117">See also</span></span>

- [<span data-ttu-id="3e507-118">Janelas de Memória</span><span class="sxs-lookup"><span data-stu-id="3e507-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)

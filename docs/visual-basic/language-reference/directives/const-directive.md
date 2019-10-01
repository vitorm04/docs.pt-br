---
title: '#Diretiva Const (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 9b8d2da2158a8244b4533eb6ef49049949417216
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696849"
---
# <a name="const-directive"></a><span data-ttu-id="e857b-102">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="e857b-102">#Const Directive</span></span>
<span data-ttu-id="e857b-103">Define constantes de compilador condicional para Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e857b-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e857b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e857b-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e857b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e857b-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="e857b-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e857b-106">Required.</span></span> <span data-ttu-id="e857b-107">Nome da constante que está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="e857b-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="e857b-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e857b-108">Required.</span></span> <span data-ttu-id="e857b-109">Literal, outra constante de compilador condicional ou qualquer combinação que inclua qualquer ou todos os operadores aritméticos ou lógicos, exceto `Is`.</span><span class="sxs-lookup"><span data-stu-id="e857b-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e857b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e857b-110">Remarks</span></span>  
 <span data-ttu-id="e857b-111">Constantes de compilador condicional são sempre particulares para o arquivo no qual aparecem.</span><span class="sxs-lookup"><span data-stu-id="e857b-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="e857b-112">Você não pode criar constantes de compilador público usando a diretiva `#Const`; Você pode criá-los somente na interface do usuário ou com a opção de compilador `/define`.</span><span class="sxs-lookup"><span data-stu-id="e857b-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="e857b-113">Você pode usar apenas constantes de compilador condicionais e literais no `expression`.</span><span class="sxs-lookup"><span data-stu-id="e857b-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="e857b-114">O uso de uma constante padrão definida com `Const` causa um erro.</span><span class="sxs-lookup"><span data-stu-id="e857b-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="e857b-115">Por outro lado, você pode usar constantes definidas com a palavra-chave `#Const` somente para compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="e857b-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="e857b-116">As constantes também podem ser indefinidas; nesse caso, elas têm um valor de `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e857b-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e857b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e857b-117">Example</span></span>  
 <span data-ttu-id="e857b-118">Este exemplo usa a diretiva `#Const`.</span><span class="sxs-lookup"><span data-stu-id="e857b-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e857b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e857b-119">See also</span></span>

- [<span data-ttu-id="e857b-120">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e857b-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
- [<span data-ttu-id="e857b-121">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="e857b-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="e857b-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="e857b-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="e857b-123">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="e857b-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="e857b-124">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="e857b-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

---
title: '#If... Then... #Else diretivas'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591075"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="13f74-102">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="13f74-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="13f74-103">Compila condicionalmente blocos de código do Visual Basic selecionados.</span><span class="sxs-lookup"><span data-stu-id="13f74-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13f74-104">Syntax</span></span>  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a><span data-ttu-id="13f74-105">Partes</span><span class="sxs-lookup"><span data-stu-id="13f74-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="13f74-106">Necessário para `#If` e `#ElseIf` instruções, opcionais em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="13f74-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="13f74-107">Qualquer expressão, consistindo exclusivamente de uma ou mais constantes condicionais de compilador, literais e operadores, que é avaliada como `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="13f74-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="13f74-108">Necessário para `#If` bloco de declaração, opcional em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="13f74-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="13f74-109">Visual Basic programa linhas ou diretivas de compilador que são compiladas se a expressão associada for avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="13f74-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="13f74-110">Encerra o `#If` bloco de instrução.</span><span class="sxs-lookup"><span data-stu-id="13f74-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13f74-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="13f74-111">Remarks</span></span>  
 <span data-ttu-id="13f74-112">Na superfície, o comportamento do `#If...Then...#Else` diretivas aparece o mesmo que o `If...Then...Else` instruções.</span><span class="sxs-lookup"><span data-stu-id="13f74-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="13f74-113">No entanto, o `#If...Then...#Else` avaliam o que é compilado pelo compilador, enquanto o `If...Then...Else` instruções avaliam condições em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="13f74-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="13f74-114">Compilação condicional é normalmente usada para compilar o mesmo programa para diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="13f74-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="13f74-115">Ele também é usado para evitar a depuração de código seja exibido em um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="13f74-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="13f74-116">Código excluído durante compilação condicional é completamente omitido do arquivo executável final, para que ele não tem nenhum efeito no tamanho ou desempenho.</span><span class="sxs-lookup"><span data-stu-id="13f74-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="13f74-117">Independentemente do resultado de qualquer avaliação, todas as expressões são avaliadas usando `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="13f74-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="13f74-118">O `Option Compare` instrução não afeta as expressões nas `#If` e `#ElseIf` instruções.</span><span class="sxs-lookup"><span data-stu-id="13f74-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13f74-119">Nenhuma forma de linha única do `#If`, `#Else`, `#ElseIf`, e `#End If` diretivas existe.</span><span class="sxs-lookup"><span data-stu-id="13f74-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="13f74-120">Nenhum outro código pode aparecer na mesma linha como qualquer das diretivas.</span><span class="sxs-lookup"><span data-stu-id="13f74-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="13f74-121">As instruções dentro de um bloco de compilação condicional devem ser concluída lógico.</span><span class="sxs-lookup"><span data-stu-id="13f74-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="13f74-122">Por exemplo, você não pode compilar condicionalmente apenas os atributos de uma função, mas condicionalmente, você pode declarar a função juntamente com seus atributos:</span><span class="sxs-lookup"><span data-stu-id="13f74-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="13f74-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13f74-123">Example</span></span>
 <span data-ttu-id="13f74-124">Este exemplo usa o `#If...Then...#Else` construção para determinar se deve compilar certas declarações.</span><span class="sxs-lookup"><span data-stu-id="13f74-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="13f74-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13f74-125">See Also</span></span>  
[<span data-ttu-id="13f74-126">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="13f74-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
[<span data-ttu-id="13f74-127">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="13f74-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
<span data-ttu-id="13f74-128">[Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="13f74-128">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   



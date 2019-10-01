---
title: '#Se... Diretivas then... #Else (Visual Basic)'
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
ms.openlocfilehash: c5357dca24b03ddd03779866019baf14175be992
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698542"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="0badb-102">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="0badb-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="0badb-103">Compila condicionalmente os blocos selecionados de código de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0badb-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0badb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0badb-104">Syntax</span></span>  
  
```vb  
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
  
## <a name="parts"></a><span data-ttu-id="0badb-105">Partes</span><span class="sxs-lookup"><span data-stu-id="0badb-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="0badb-106">Necessário para instruções `#If` e `#ElseIf`, opcional em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="0badb-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="0badb-107">Qualquer expressão, consistindo exclusivamente em uma ou mais constantes de compilador condicionais, literais e operadores, que é avaliada como `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="0badb-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="0badb-108">Necessário para bloco de instruções `#If`, opcional em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="0badb-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="0badb-109">Visual Basic linhas de programa ou diretivas de compilador que são compiladas se a expressão associada for avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="0badb-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="0badb-110">Encerra o bloco de instruções `#If`.</span><span class="sxs-lookup"><span data-stu-id="0badb-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0badb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0badb-111">Remarks</span></span>  
 <span data-ttu-id="0badb-112">Na superfície, o comportamento das diretivas `#If...Then...#Else` é exibido da mesma forma que as instruções `If...Then...Else`.</span><span class="sxs-lookup"><span data-stu-id="0badb-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="0badb-113">No entanto, as diretivas `#If...Then...#Else` avaliam o que é compilado pelo compilador, enquanto as instruções `If...Then...Else` avaliam condições em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0badb-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="0badb-114">A compilação condicional é normalmente usada para compilar o mesmo programa para diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="0badb-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="0badb-115">Ele também é usado para impedir que o código de depuração apareça em um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="0badb-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="0badb-116">O código excluído durante a compilação condicional é completamente omitido do arquivo executável final, portanto, não tem efeito sobre o tamanho ou o desempenho.</span><span class="sxs-lookup"><span data-stu-id="0badb-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="0badb-117">Independentemente do resultado de qualquer avaliação, todas as expressões são avaliadas usando `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="0badb-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="0badb-118">A instrução `Option Compare` não afeta as expressões nas instruções `#If` e `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="0badb-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0badb-119">Não existe um formulário de linha única das diretivas `#If`, `#Else`, `#ElseIf` e `#End If`.</span><span class="sxs-lookup"><span data-stu-id="0badb-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="0badb-120">Nenhum outro código pode aparecer na mesma linha que qualquer uma das diretivas.</span><span class="sxs-lookup"><span data-stu-id="0badb-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="0badb-121">As instruções em um bloco de compilação condicional devem ser instruções lógicas completas.</span><span class="sxs-lookup"><span data-stu-id="0badb-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="0badb-122">Por exemplo, você não pode compilar condicionalmente apenas os atributos de uma função, mas pode declarar condicionalmente a função junto com seus atributos:</span><span class="sxs-lookup"><span data-stu-id="0badb-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="0badb-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0badb-123">Example</span></span>
 <span data-ttu-id="0badb-124">Este exemplo usa a construção `#If...Then...#Else` para determinar se deve compilar determinadas instruções.</span><span class="sxs-lookup"><span data-stu-id="0badb-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0badb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0badb-125">See also</span></span>

- [<span data-ttu-id="0badb-126">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="0badb-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="0badb-127">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="0badb-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="0badb-128">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="0badb-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>

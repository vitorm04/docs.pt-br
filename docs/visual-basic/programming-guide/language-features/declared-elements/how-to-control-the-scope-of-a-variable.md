---
title: 'Como: Controlar o escopo de uma variável (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: ef7957a991718112fe01c4fa3a85f29b9226abd3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818717"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="16c96-102">Como: Controlar o escopo de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16c96-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="16c96-103">Normalmente, uma variável está no *escopo*, ou visível para referência, em toda a região na qual você declará-la.</span><span class="sxs-lookup"><span data-stu-id="16c96-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="16c96-104">Em alguns casos, a variável *nível de acesso* podem influenciar seu escopo.</span><span class="sxs-lookup"><span data-stu-id="16c96-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="16c96-105">Para obter mais informações, consulte [escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="16c96-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="16c96-106">Escopo no nível de procedimento ou bloco</span><span class="sxs-lookup"><span data-stu-id="16c96-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="16c96-107">Para fazer uma variável visível somente dentro de um bloco</span><span class="sxs-lookup"><span data-stu-id="16c96-107">To make a variable visible only within a block</span></span>  
  
-   <span data-ttu-id="16c96-108">Coloque o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável entre o Iniciando e encerrando instruções de declaração desse bloco, por exemplo, entre a `For` e `Next` instruções de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="16c96-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="16c96-109">Você pode fazer referência à variável apenas de dentro do bloco.</span><span class="sxs-lookup"><span data-stu-id="16c96-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="16c96-110">Para fazer uma variável visível somente dentro de um procedimento</span><span class="sxs-lookup"><span data-stu-id="16c96-110">To make a variable visible only within a procedure</span></span>  
  
-   <span data-ttu-id="16c96-111">Coloque o `Dim` instrução para a variável dentro do procedimento, mas fora de qualquer bloco (como um `With`... `End With` bloco).</span><span class="sxs-lookup"><span data-stu-id="16c96-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="16c96-112">Você pode fazer referência à variável apenas de dentro do procedimento, inclusive dentro de qualquer bloco contido no procedimento.</span><span class="sxs-lookup"><span data-stu-id="16c96-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="16c96-113">Escopo no nível de Namespace ou módulo</span><span class="sxs-lookup"><span data-stu-id="16c96-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="16c96-114">Para sua conveniência, o termo simples *nível de módulo* se aplica igualmente a módulos, classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="16c96-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="16c96-115">O nível de acesso de uma variável de nível de módulo determina seu escopo.</span><span class="sxs-lookup"><span data-stu-id="16c96-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="16c96-116">O namespace que contém o módulo, classe ou estrutura também influencia o escopo.</span><span class="sxs-lookup"><span data-stu-id="16c96-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="16c96-117">Para tornar uma variável visível em um módulo, classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="16c96-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1.  <span data-ttu-id="16c96-118">Coloque o `Dim` instrução para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="16c96-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="16c96-119">Incluir o [privados](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="16c96-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3.  <span data-ttu-id="16c96-120">Você pode fazer referência à variável de qualquer lugar dentro do módulo, classe ou estrutura, mas não de fora dela.</span><span class="sxs-lookup"><span data-stu-id="16c96-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="16c96-121">Para tornar uma variável visível em um namespace</span><span class="sxs-lookup"><span data-stu-id="16c96-121">To make a variable visible throughout a namespace</span></span>  
  
1.  <span data-ttu-id="16c96-122">Coloque o `Dim` instrução para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="16c96-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="16c96-123">Incluir o [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) ou [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="16c96-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3.  <span data-ttu-id="16c96-124">Você pode fazer referência à variável de qualquer lugar dentro do namespace que contém o módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="16c96-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16c96-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16c96-125">Example</span></span>  
 <span data-ttu-id="16c96-126">O exemplo a seguir declara uma variável no nível de módulo e limita sua visibilidade ao código dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="16c96-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="16c96-127">No exemplo anterior, todos os procedimentos definidos no módulo `demonstrateScope` pode se referir a `String` variável `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="16c96-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="16c96-128">Quando o `usePrivateVariable` procedimento é chamado, ele exibe o conteúdo da variável de cadeia de caracteres `strMsg` em uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="16c96-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="16c96-129">Com a seguinte alteração ao exemplo anterior, a variável de cadeia de caracteres `strMsg` pode ser chamada pelo código em qualquer lugar no namespace da sua declaração.</span><span class="sxs-lookup"><span data-stu-id="16c96-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="16c96-130">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="16c96-130">Robust Programming</span></span>  
 <span data-ttu-id="16c96-131">Quanto mais estreito o escopo de uma variável, e menos oportunidades que você tem para se referir acidentalmente a ele no lugar de outra variável com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="16c96-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="16c96-132">Você também pode minimizar problemas de referência correspondente.</span><span class="sxs-lookup"><span data-stu-id="16c96-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="16c96-133">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="16c96-133">.NET Framework Security</span></span>  
 <span data-ttu-id="16c96-134">Quanto mais estreito o escopo de uma variável, menores as chances de que um código mal-intencionado pode fazer inadequado usá-lo.</span><span class="sxs-lookup"><span data-stu-id="16c96-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c96-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16c96-135">See also</span></span>

- [<span data-ttu-id="16c96-136">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16c96-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="16c96-137">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16c96-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="16c96-138">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16c96-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="16c96-139">Variáveis</span><span class="sxs-lookup"><span data-stu-id="16c96-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="16c96-140">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="16c96-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="16c96-141">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="16c96-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)

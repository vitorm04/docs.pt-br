---
title: Como controlar o escopo de uma variável
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
ms.openlocfilehash: 2ce7c1700eec54542719e6e0880466ca136e86f6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095419"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="aee28-102">Como controlar o escopo de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aee28-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>

<span data-ttu-id="aee28-103">Normalmente, uma variável está no *escopo*ou visível para referência, em toda a região em que você a declara.</span><span class="sxs-lookup"><span data-stu-id="aee28-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="aee28-104">Em alguns casos, o nível de *acesso* da variável pode influenciar seu escopo.</span><span class="sxs-lookup"><span data-stu-id="aee28-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="aee28-105">Para obter mais informações, consulte [escopo em Visual Basic](scope.md).</span><span class="sxs-lookup"><span data-stu-id="aee28-105">For more information, see [Scope in Visual Basic](scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="aee28-106">Escopo no nível de bloco ou procedimento</span><span class="sxs-lookup"><span data-stu-id="aee28-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="aee28-107">Para tornar uma variável visível somente dentro de um bloco</span><span class="sxs-lookup"><span data-stu-id="aee28-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="aee28-108">Coloque a [instrução Dim](../../../language-reference/statements/dim-statement.md) para a variável entre as instruções de declaração de inicialização e término desse bloco, por exemplo, entre as `For` `Next` instruções e de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="aee28-108">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="aee28-109">Você pode se referir à variável somente de dentro do bloco.</span><span class="sxs-lookup"><span data-stu-id="aee28-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="aee28-110">Para tornar uma variável visível somente dentro de um procedimento</span><span class="sxs-lookup"><span data-stu-id="aee28-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="aee28-111">Coloque a `Dim` instrução para a variável dentro do procedimento, mas fora de qualquer bloco (como um `With` bloco... `End With` ).</span><span class="sxs-lookup"><span data-stu-id="aee28-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="aee28-112">Você pode se referir à variável somente de dentro do procedimento, incluindo dentro de qualquer bloco contido no procedimento.</span><span class="sxs-lookup"><span data-stu-id="aee28-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="aee28-113">Escopo no nível de namespace ou módulo</span><span class="sxs-lookup"><span data-stu-id="aee28-113">Scope at Module or Namespace Level</span></span>  

 <span data-ttu-id="aee28-114">Para sua conveniência, o *nível de módulo* de termo único aplica-se igualmente a módulos, classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="aee28-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="aee28-115">O nível de acesso de uma variável de nível de módulo determina seu escopo.</span><span class="sxs-lookup"><span data-stu-id="aee28-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="aee28-116">O namespace que contém o módulo, a classe ou a estrutura também influencia o escopo.</span><span class="sxs-lookup"><span data-stu-id="aee28-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="aee28-117">Para tornar uma variável visível em um módulo, classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="aee28-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="aee28-118">Coloque a `Dim` instrução para a variável dentro do módulo, da classe ou da estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="aee28-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="aee28-119">Inclua a palavra-chave [Private](../../../language-reference/modifiers/private.md) na `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="aee28-119">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="aee28-120">Você pode consultar a variável de qualquer lugar dentro do módulo, da classe ou da estrutura, mas não de fora dela.</span><span class="sxs-lookup"><span data-stu-id="aee28-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="aee28-121">Para tornar uma variável visível em um namespace</span><span class="sxs-lookup"><span data-stu-id="aee28-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="aee28-122">Coloque a `Dim` instrução para a variável dentro do módulo, da classe ou da estrutura, mas fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="aee28-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="aee28-123">Inclua a palavra-chave [Friend](../../../language-reference/modifiers/friend.md) ou [Public](../../../language-reference/modifiers/public.md) na `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="aee28-123">Include the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="aee28-124">Você pode consultar a variável de qualquer lugar dentro do namespace que contém o módulo, a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="aee28-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aee28-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aee28-125">Example</span></span>  

 <span data-ttu-id="aee28-126">O exemplo a seguir declara uma variável no nível do módulo e limita sua visibilidade ao código dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="aee28-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="aee28-127">No exemplo anterior, todos os procedimentos definidos no módulo `demonstrateScope` podem se referir à `String` variável `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="aee28-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="aee28-128">Quando o `usePrivateVariable` procedimento é chamado, ele exibe o conteúdo da variável de cadeia de caracteres `strMsg` em uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="aee28-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="aee28-129">Com a seguinte alteração no exemplo anterior, a variável de cadeia de caracteres `strMsg` pode ser referenciada pelo código em qualquer lugar no namespace de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="aee28-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="aee28-130">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="aee28-130">Robust Programming</span></span>  

 <span data-ttu-id="aee28-131">Quanto mais estreita for o escopo de uma variável, menos oportunidades você terá para se referir acidentalmente a ela em vez de outra variável com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="aee28-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="aee28-132">Você também pode minimizar problemas de correspondência de referência.</span><span class="sxs-lookup"><span data-stu-id="aee28-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="aee28-133">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aee28-133">.NET Framework Security</span></span>  

 <span data-ttu-id="aee28-134">Quanto mais estreita for o escopo de uma variável, menor será a probabilidade de que o código mal-intencionado possa fazer uso impróprio dela.</span><span class="sxs-lookup"><span data-stu-id="aee28-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee28-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="aee28-135">See also</span></span>

- [<span data-ttu-id="aee28-136">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aee28-136">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="aee28-137">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aee28-137">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="aee28-138">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aee28-138">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="aee28-139">Variáveis</span><span class="sxs-lookup"><span data-stu-id="aee28-139">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="aee28-140">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="aee28-140">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="aee28-141">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="aee28-141">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)

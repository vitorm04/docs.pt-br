---
title: Variável de objeto ou variável com bloco não definida
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e1f587e194acf744b6ec9b8f1bede3acef7b753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="ce018-102">Variável de objeto ou variável com bloco não definida</span><span class="sxs-lookup"><span data-stu-id="ce018-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="ce018-103">Uma variável de objeto inválida está sendo referenciada.</span><span class="sxs-lookup"><span data-stu-id="ce018-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="ce018-104">Esse erro pode ocorrer por várias razões:</span><span class="sxs-lookup"><span data-stu-id="ce018-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="ce018-105">Uma variável foi declarada sem especificar um tipo.</span><span class="sxs-lookup"><span data-stu-id="ce018-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="ce018-106">Se uma variável é declarada sem especificar um tipo, o padrão é para o tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="ce018-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="ce018-107">Por exemplo, uma variável declarada com `Dim x` deve ser do tipo `Object;` uma variável declarada com `Dim x As String` deve ser do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="ce018-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="ce018-108">O `Option Strict` instrução não permite digitar implícita que resulta em um `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="ce018-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="ce018-109">Se você omitir o tipo, ocorrerá um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ce018-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="ce018-110">Consulte [opção Strict instrução](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce018-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="ce018-111">Você está tentando fazer referência a um objeto que foi definido como`Nothing`</span><span class="sxs-lookup"><span data-stu-id="ce018-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="ce018-112">.</span><span class="sxs-lookup"><span data-stu-id="ce018-112">.</span></span>  
  
-   <span data-ttu-id="ce018-113">Você está tentando acessar um elemento de uma variável de matriz não foi declarado corretamente.</span><span class="sxs-lookup"><span data-stu-id="ce018-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="ce018-114">Por exemplo, uma matriz declarada como `products() As String` disparará o erro se você tentar fazer referência a um elemento da matriz `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="ce018-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="ce018-115">A matriz não tem elementos e é tratada como um objeto.</span><span class="sxs-lookup"><span data-stu-id="ce018-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="ce018-116">Tentativa de acesso de código dentro de um `With...End With` bloquear antes que o bloco foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="ce018-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="ce018-117">Um `With...End With` deve ser inicializado executando o `With` ponto de entrada de instrução.</span><span class="sxs-lookup"><span data-stu-id="ce018-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce018-118">Em versões anteriores do Visual Basic ou VBA esse erro também foi disparado, atribuindo um valor a uma variável sem usar o `Set` palavra-chave (`x = "name"` em vez de `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="ce018-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="ce018-119">O `Set` palavra-chave não é válida no Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="ce018-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ce018-120">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ce018-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="ce018-121">Definir `Option Strict` para `On` adicionando o código a seguir para o início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="ce018-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="ce018-122">Se você não quiser habilitar `Option Strict`, pesquise o código para todas as variáveis que foram especificadas sem um tipo (`Dim x` em vez de `Dim x As String`) e adicione o tipo desejado para a declaração.</span><span class="sxs-lookup"><span data-stu-id="ce018-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="ce018-123">Verifique se você não está fazendo referência a uma variável de objeto que foi definida como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ce018-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="ce018-124">Pesquise o código para a palavra-chave `Nothing`e revisar seu código para que o objeto não está definido como `Nothing` até após você ter referenciado.</span><span class="sxs-lookup"><span data-stu-id="ce018-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="ce018-125">Certifique-se de que quaisquer variáveis de matriz são dimensionadas para acessá-los.</span><span class="sxs-lookup"><span data-stu-id="ce018-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="ce018-126">Você pode atribuir uma dimensão quando você cria a matriz (`Dim x(5) As String` em vez de `Dim x() As String`), ou use o `ReDim` palavra-chave para definir as dimensões da matriz antes de acessar pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="ce018-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="ce018-127">Certifique-se de sua `With` bloco é inicializado executando o `With` ponto de entrada de instrução.</span><span class="sxs-lookup"><span data-stu-id="ce018-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce018-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce018-128">See Also</span></span>  
 [<span data-ttu-id="ce018-129">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="ce018-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="ce018-130">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="ce018-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="ce018-131">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="ce018-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

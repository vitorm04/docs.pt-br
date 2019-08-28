---
title: Variável de objeto ou variável com bloco não definida
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040552"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="5e0d7-102">Variável de objeto ou variável com bloco não definida</span><span class="sxs-lookup"><span data-stu-id="5e0d7-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="5e0d7-103">Uma variável de objeto inválida está sendo referenciada.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="5e0d7-104">Esse erro pode ocorrer por várias razões:</span><span class="sxs-lookup"><span data-stu-id="5e0d7-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="5e0d7-105">Uma variável foi declarada sem especificar um tipo.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="5e0d7-106">Se uma variável for declarada sem especificar um tipo, o padrão será `Object`Type.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="5e0d7-107">Por exemplo, uma `Dim x` variável declarada com seria do tipo `Object;` uma variável declarada com `Dim x As String` seria `String`do tipo.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="5e0d7-108">A `Option Strict` instrução não permite a digitação implícita que resulta em `Object` um tipo.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="5e0d7-109">Se você omitir o tipo, ocorrerá um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="5e0d7-110">Consulte a [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e0d7-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="5e0d7-111">Você está tentando fazer referência a um objeto que foi definido como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="5e0d7-112">Você está tentando acessar um elemento de uma variável de matriz que não foi declarada corretamente.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="5e0d7-113">Por exemplo, uma matriz declarada como `products() As String` irá disparar o erro se você tentar fazer referência a um elemento da matriz. `products(3) = "Widget"`</span><span class="sxs-lookup"><span data-stu-id="5e0d7-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="5e0d7-114">A matriz não tem elementos e é tratada como um objeto.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="5e0d7-115">Você está tentando acessar o código dentro de um `With...End With` bloco antes que o bloco tenha sido inicializado.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="5e0d7-116">Um `With...End With` bloco deve ser inicializado executando o `With` ponto de entrada da instrução.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="5e0d7-117">Em versões anteriores do Visual Basic ou do VBA, esse erro também foi disparado por meio da atribuição de um valor a `Set` uma variável`x = "name"` sem usar `Set x = "name"`a palavra-chave (em vez de).</span><span class="sxs-lookup"><span data-stu-id="5e0d7-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="5e0d7-118">A `Set` palavra-chave não é mais válida no Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5e0d7-119">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5e0d7-119">To correct this error</span></span>

1. <span data-ttu-id="5e0d7-120">Defina `Option Strict` como`On` adicionando o seguinte código ao início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="5e0d7-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="5e0d7-121">Quando você executar o projeto, um erro do compilador será exibido no **lista de erros** para qualquer variável que foi especificada sem um tipo.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="5e0d7-122">Se você não quiser habilitar `Option Strict`o, pesquise o código em busca de variáveis que foram especificadas sem um tipo (`Dim x` em `Dim x As String`vez de) e adicione o tipo pretendido à declaração.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="5e0d7-123">Verifique se você não está se referindo a uma variável de objeto que `Nothing`foi definida como.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="5e0d7-124">Pesquise seu código para a palavra `Nothing`-chave e revise seu código para que o objeto não seja `Nothing` definido como até que você o tenha referenciado.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="5e0d7-125">Certifique-se de que todas as variáveis de matriz sejam dimensionadas antes de acessá-las.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="5e0d7-126">Você pode atribuir uma dimensão quando criar a matriz (`Dim x(5) As String` em vez de), ou usar a `ReDim` palavra-chave para definir as dimensões da matriz antes de `Dim x() As String`acessá-la pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="5e0d7-127">Verifique se o `With` bloco foi inicializado executando o `With` ponto de entrada da instrução.</span><span class="sxs-lookup"><span data-stu-id="5e0d7-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e0d7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e0d7-128">See also</span></span>

- [<span data-ttu-id="5e0d7-129">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="5e0d7-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="5e0d7-130">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="5e0d7-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="5e0d7-131">Instrução With ... End With</span><span class="sxs-lookup"><span data-stu-id="5e0d7-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

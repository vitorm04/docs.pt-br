---
title: Variável de objeto ou variável com bloco não definida
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 0264a4235a056c93edb703ec2ef70e7124e0df4e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873627"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="51798-102">Variável de objeto ou variável com bloco não definida</span><span class="sxs-lookup"><span data-stu-id="51798-102">Object variable or With block variable not set</span></span>

<span data-ttu-id="51798-103">Uma variável de objeto inválida está sendo referenciada.</span><span class="sxs-lookup"><span data-stu-id="51798-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="51798-104">Esse erro pode ocorrer por várias razões:</span><span class="sxs-lookup"><span data-stu-id="51798-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="51798-105">Uma variável foi declarada sem especificar um tipo.</span><span class="sxs-lookup"><span data-stu-id="51798-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="51798-106">Se uma variável for declarada sem especificar um tipo, o padrão será Type `Object` .</span><span class="sxs-lookup"><span data-stu-id="51798-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="51798-107">Por exemplo, uma variável declarada com `Dim x` seria do tipo `Object;` uma variável declarada com `Dim x As String` seria do tipo `String` .</span><span class="sxs-lookup"><span data-stu-id="51798-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="51798-108">A `Option Strict` instrução não permite a digitação implícita que resulta em um `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="51798-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="51798-109">Se você omitir o tipo, ocorrerá um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="51798-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="51798-110">Consulte a [instrução Option Strict](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="51798-110">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="51798-111">Você está tentando fazer referência a um objeto que foi definido como `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="51798-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="51798-112">Você está tentando acessar um elemento de uma variável de matriz que não foi declarada corretamente.</span><span class="sxs-lookup"><span data-stu-id="51798-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="51798-113">Por exemplo, uma matriz declarada como `products() As String` irá disparar o erro se você tentar fazer referência a um elemento da matriz `products(3) = "Widget"` .</span><span class="sxs-lookup"><span data-stu-id="51798-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="51798-114">A matriz não tem elementos e é tratada como um objeto.</span><span class="sxs-lookup"><span data-stu-id="51798-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="51798-115">Você está tentando acessar o código dentro de um `With...End With` bloco antes que o bloco tenha sido inicializado.</span><span class="sxs-lookup"><span data-stu-id="51798-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="51798-116">Um `With...End With` bloco deve ser inicializado executando o `With` ponto de entrada da instrução.</span><span class="sxs-lookup"><span data-stu-id="51798-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="51798-117">Em versões anteriores do Visual Basic ou do VBA, esse erro também foi disparado por meio da atribuição de um valor a uma variável sem usar a `Set` palavra-chave ( `x = "name"` em vez de `Set x = "name"` ).</span><span class="sxs-lookup"><span data-stu-id="51798-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="51798-118">A `Set` palavra-chave não é mais válida no Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="51798-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="51798-119">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="51798-119">To correct this error</span></span>

1. <span data-ttu-id="51798-120">Defina `Option Strict` como `On` adicionando o seguinte código ao início do arquivo:</span><span class="sxs-lookup"><span data-stu-id="51798-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="51798-121">Quando você executar o projeto, um erro do compilador será exibido no **lista de erros** para qualquer variável que foi especificada sem um tipo.</span><span class="sxs-lookup"><span data-stu-id="51798-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="51798-122">Se você não quiser habilitar `Option Strict` o, pesquise o código em busca de variáveis que foram especificadas sem um tipo ( `Dim x` em vez de `Dim x As String` ) e adicione o tipo pretendido à declaração.</span><span class="sxs-lookup"><span data-stu-id="51798-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="51798-123">Verifique se você não está se referindo a uma variável de objeto que foi definida como `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="51798-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="51798-124">Pesquise seu código para a palavra-chave `Nothing` e revise seu código para que o objeto não seja definido como `Nothing` até que você o tenha referenciado.</span><span class="sxs-lookup"><span data-stu-id="51798-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="51798-125">Certifique-se de que todas as variáveis de matriz sejam dimensionadas antes de acessá-las.</span><span class="sxs-lookup"><span data-stu-id="51798-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="51798-126">Você pode atribuir uma dimensão quando criar a matriz ( `Dim x(5) As String` em vez de `Dim x() As String` ), ou usar a `ReDim` palavra-chave para definir as dimensões da matriz antes de acessá-la pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="51798-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="51798-127">Verifique se o `With` bloco foi inicializado executando o `With` ponto de entrada da instrução.</span><span class="sxs-lookup"><span data-stu-id="51798-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="51798-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="51798-128">See also</span></span>

- [<span data-ttu-id="51798-129">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="51798-129">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="51798-130">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="51798-130">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="51798-131">Instrução With...End With</span><span class="sxs-lookup"><span data-stu-id="51798-131">With...End With Statement</span></span>](../statements/with-end-with-statement.md)

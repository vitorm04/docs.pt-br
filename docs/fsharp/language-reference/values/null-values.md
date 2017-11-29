---
title: Valores nulos (F#)
description: "Saiba como o valor nulo é usado em F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 68ebd261-51cf-4582-b2dc-44c84d1c2500
ms.openlocfilehash: 01c14de00eb5efd0952145ffc8aabe69d65a3a48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="null-values"></a><span data-ttu-id="ac587-104">Valores nulos</span><span class="sxs-lookup"><span data-stu-id="ac587-104">Null Values</span></span>

<span data-ttu-id="ac587-105">Este tópico descreve como o valor nulo é usado em F #.</span><span class="sxs-lookup"><span data-stu-id="ac587-105">This topic describes how the null value is used in F#.</span></span>


## <a name="null-value"></a><span data-ttu-id="ac587-106">Valor nulo</span><span class="sxs-lookup"><span data-stu-id="ac587-106">Null Value</span></span>
<span data-ttu-id="ac587-107">O valor nulo não é usado normalmente em F # para valores ou variáveis.</span><span class="sxs-lookup"><span data-stu-id="ac587-107">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="ac587-108">No entanto, null é exibido como um valor anormal em determinadas situações.</span><span class="sxs-lookup"><span data-stu-id="ac587-108">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="ac587-109">Se um tipo é definido em F #, null não é permitido como um valor regular, a menos que o [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atributo é aplicado ao tipo.</span><span class="sxs-lookup"><span data-stu-id="ac587-109">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) attribute is applied to the type.</span></span> <span data-ttu-id="ac587-110">Se um tipo é definido em alguma outra linguagem .NET, null é um valor possível e, quando você está interoperando com esses tipos, seu código F # pode ser encontrados valores nulos.</span><span class="sxs-lookup"><span data-stu-id="ac587-110">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="ac587-111">Para um tipo definido em F # e usados unicamente do F #, a única maneira de criar um valor nulo usando a biblioteca F # diretamente é usar [unchecked. defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) ou [zerocreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span><span class="sxs-lookup"><span data-stu-id="ac587-111">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) or [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span></span> <span data-ttu-id="ac587-112">No entanto, para um tipo de F #, que é usado em outras linguagens .NET, ou se você estiver usando esse tipo com uma API que não é gravada em F #, como o .NET Framework, valores nulos podem ocorrer.</span><span class="sxs-lookup"><span data-stu-id="ac587-112">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="ac587-113">Você pode usar o `option` tipo em F # quando você pode usar uma variável de referência com um valor nulo possíveis em outra linguagem .NET.</span><span class="sxs-lookup"><span data-stu-id="ac587-113">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="ac587-114">Em vez de null, com um F # `option` tipo, use o valor da opção `None` se não houver nenhum objeto.</span><span class="sxs-lookup"><span data-stu-id="ac587-114">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="ac587-115">Use o valor da opção `Some(obj)` com um objeto `obj` quando há um objeto.</span><span class="sxs-lookup"><span data-stu-id="ac587-115">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="ac587-116">Para obter mais informações, consulte [opções](../options.md).</span><span class="sxs-lookup"><span data-stu-id="ac587-116">For more information, see [Options](../options.md).</span></span>

<span data-ttu-id="ac587-117">O `null` palavra-chave é uma palavra-chave válida na linguagem F # e desejar usá-lo quando você estiver trabalhando com APIs do .NET Framework ou outras APIs que são escritos em outra linguagem .NET.</span><span class="sxs-lookup"><span data-stu-id="ac587-117">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="ac587-118">As duas situações em que talvez seja necessário um valor nulo são quando você chamar uma API .NET e passa um valor nulo como um argumento e interpretar o valor de retorno ou parâmetro de saída uma chamada de método do .NET.</span><span class="sxs-lookup"><span data-stu-id="ac587-118">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="ac587-119">Para passar um valor nulo para um método do .NET, use o `null` palavra-chave no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="ac587-119">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="ac587-120">O exemplo de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="ac587-120">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="ac587-121">Para interpretar um valor nulo que é obtido a partir de um método do .NET, use a correspondência de padrões, se possível.</span><span class="sxs-lookup"><span data-stu-id="ac587-121">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="ac587-122">O exemplo de código a seguir mostra como usar a correspondência de padrões para interpretar o valor nulo é retornado de `ReadLine` quando ele tenta ler após o término de um fluxo de entrada.</span><span class="sxs-lookup"><span data-stu-id="ac587-122">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="ac587-123">Valores nulos para tipos F # também podem ser gerados de outras maneiras, como quando você usa `Array.zeroCreate`, que chama `Unchecked.defaultof`.</span><span class="sxs-lookup"><span data-stu-id="ac587-123">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="ac587-124">Você deve ter cuidado com o código, para manter os valores nulos encapsulados.</span><span class="sxs-lookup"><span data-stu-id="ac587-124">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="ac587-125">Em uma biblioteca destinada apenas para F #, você não precisa verificar se há valores nulos em cada função.</span><span class="sxs-lookup"><span data-stu-id="ac587-125">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="ac587-126">Se você estiver gravando uma biblioteca para a interoperação com outras linguagens .NET, talvez você precise adicionar procura null parâmetros de entrada e gera um `ArgumentNullException`, assim como faria em código c# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac587-126">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="ac587-127">Você pode usar o código a seguir para verificar se um valor arbitrário é nulo.</span><span class="sxs-lookup"><span data-stu-id="ac587-127">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="ac587-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac587-128">See Also</span></span>
[<span data-ttu-id="ac587-129">Valores</span><span class="sxs-lookup"><span data-stu-id="ac587-129">Values</span></span>](index.md)

[<span data-ttu-id="ac587-130">Expressões Match</span><span class="sxs-lookup"><span data-stu-id="ac587-130">Match Expressions</span></span>](../match-expressions.md)

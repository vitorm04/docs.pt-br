---
title: Namespaces (F#)
description: 'Saiba como um namespace do F # permite organizar o código em áreas de funcionalidades relacionadas, permitindo que você anexar um nome a um grupo de elementos do programa.'
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 695de3b58b8567da60c8ef86900f8e78ea563e0e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="namespaces"></a><span data-ttu-id="cc474-103">Namespaces</span><span class="sxs-lookup"><span data-stu-id="cc474-103">Namespaces</span></span>

<span data-ttu-id="cc474-104">Um namespace permite organizar o código em áreas de funcionalidade relacionada ao permitir que você anexe um nome a um agrupamento de elementos de programação.</span><span class="sxs-lookup"><span data-stu-id="cc474-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>


## <a name="syntax"></a><span data-ttu-id="cc474-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc474-105">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="cc474-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc474-106">Remarks</span></span>
<span data-ttu-id="cc474-107">Se você deseja colocar o código em um namespace, a primeira declaração no arquivo deve declarar o namespace.</span><span class="sxs-lookup"><span data-stu-id="cc474-107">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="cc474-108">O conteúdo de todo o arquivo se tornam parte do namespace.</span><span class="sxs-lookup"><span data-stu-id="cc474-108">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="cc474-109">Namespaces diretamente não podem conter valores e funções.</span><span class="sxs-lookup"><span data-stu-id="cc474-109">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="cc474-110">Em vez disso, valores e funções devem ser incluídas em módulos e módulos estão incluídos nos namespaces.</span><span class="sxs-lookup"><span data-stu-id="cc474-110">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="cc474-111">Namespaces pode conter tipos de módulos.</span><span class="sxs-lookup"><span data-stu-id="cc474-111">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="cc474-112">Namespaces podem ser declarados explicitamente com a palavra-chave do namespace, ou implicitamente ao declarar um módulo.</span><span class="sxs-lookup"><span data-stu-id="cc474-112">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="cc474-113">Para declarar um namespace explicitamente, use a palavra-chave namespace seguida do nome de namespace.</span><span class="sxs-lookup"><span data-stu-id="cc474-113">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="cc474-114">O exemplo a seguir mostra um arquivo de código que declara um namespace Widgets com um tipo e um módulo incluídos naquele namespace.</span><span class="sxs-lookup"><span data-stu-id="cc474-114">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="cc474-115">Se todo o conteúdo do arquivo está em um módulo, você pode também declarar namespaces implicitamente, usando o `module` palavra-chave e fornecendo o novo nome de namespace no nome do módulo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="cc474-115">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="cc474-116">O exemplo a seguir mostra um arquivo de código que declara um namespace `Widgets` e um módulo `WidgetsModule`, que contém uma função.</span><span class="sxs-lookup"><span data-stu-id="cc474-116">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="cc474-117">O código a seguir é equivalente ao código anterior, mas o módulo é uma declaração de módulo local.</span><span class="sxs-lookup"><span data-stu-id="cc474-117">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="cc474-118">Nesse caso, o namespace deve aparecer em sua própria linha.</span><span class="sxs-lookup"><span data-stu-id="cc474-118">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="cc474-119">Se for necessário mais de um módulo no mesmo arquivo em um ou mais namespaces, você deve usar declarações de módulo local.</span><span class="sxs-lookup"><span data-stu-id="cc474-119">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="cc474-120">Quando você usar declarações de módulo local, você não pode usar o namespace qualificado nas declarações de módulo.</span><span class="sxs-lookup"><span data-stu-id="cc474-120">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="cc474-121">O código a seguir mostra um arquivo que tem uma declaração de namespace e duas declarações de módulo local.</span><span class="sxs-lookup"><span data-stu-id="cc474-121">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="cc474-122">Nesse caso, os módulos estão contidos diretamente no namespace; Não há nenhum módulo criado implicitamente que tem o mesmo nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="cc474-122">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="cc474-123">Qualquer outro código no arquivo, como um `do` de associação, está no namespace, mas não nos módulos internos, para que seja necessário qualificar o membro de módulo `widgetFunction` usando o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="cc474-123">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="cc474-124">A saída deste exemplo é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="cc474-124">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="cc474-125">Para obter mais informações, consulte [módulos](modules.md).</span><span class="sxs-lookup"><span data-stu-id="cc474-125">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="cc474-126">Namespaces aninhados</span><span class="sxs-lookup"><span data-stu-id="cc474-126">Nested Namespaces</span></span>
<span data-ttu-id="cc474-127">Quando você cria um namespace aninhado, você deve qualificá-lo totalmente.</span><span class="sxs-lookup"><span data-stu-id="cc474-127">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="cc474-128">Caso contrário, você pode criar um novo namespace de nível superior.</span><span class="sxs-lookup"><span data-stu-id="cc474-128">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="cc474-129">Recuo é ignorado em declarações de namespace.</span><span class="sxs-lookup"><span data-stu-id="cc474-129">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="cc474-130">O exemplo a seguir mostra como declarar um namespace aninhado.</span><span class="sxs-lookup"><span data-stu-id="cc474-130">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="cc474-131">Namespaces em arquivos e Assemblies</span><span class="sxs-lookup"><span data-stu-id="cc474-131">Namespaces in Files and Assemblies</span></span>
<span data-ttu-id="cc474-132">Namespaces podem abranger vários arquivos em um único projeto ou compilação.</span><span class="sxs-lookup"><span data-stu-id="cc474-132">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="cc474-133">O termo *fragmento namespace* descreve a parte de um namespace que é incluído em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="cc474-133">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="cc474-134">Namespaces também pode abranger vários assemblies.</span><span class="sxs-lookup"><span data-stu-id="cc474-134">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="cc474-135">Por exemplo, o `System` namespace inclui o .NET Framework inteiro, que abrange vários assemblies e contém vários namespaces aninhados.</span><span class="sxs-lookup"><span data-stu-id="cc474-135">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>


## <a name="global-namespace"></a><span data-ttu-id="cc474-136">Namespace global</span><span class="sxs-lookup"><span data-stu-id="cc474-136">Global Namespace</span></span>
<span data-ttu-id="cc474-137">Você usa o namespace predefinido `global` para colocar os nomes do namespace de nível superior do .NET.</span><span class="sxs-lookup"><span data-stu-id="cc474-137">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="cc474-138">Você também pode usar global para referenciar o namespace .NET de nível superior, por exemplo, para resolver conflitos de nomes com outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="cc474-138">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="cc474-139">Espaços de nomes recursivos</span><span class="sxs-lookup"><span data-stu-id="cc474-139">Recursive namespaces</span></span>

<span data-ttu-id="cc474-140">4.1 F # introduz a noção de namespaces que permitem que todo o código independente ser mutuamente recursivas.</span><span class="sxs-lookup"><span data-stu-id="cc474-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="cc474-141">Isso é feito por meio de `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="cc474-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="cc474-142">O uso de `namespace rec` pode aliviar alguns problemas de não conseguir gravar código mutuamente referencial entre módulos e tipos.</span><span class="sxs-lookup"><span data-stu-id="cc474-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="cc474-143">Este é um exemplo disso:</span><span class="sxs-lookup"><span data-stu-id="cc474-143">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set
    
    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="cc474-144">Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` ambos referem-se entre si.</span><span class="sxs-lookup"><span data-stu-id="cc474-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="cc474-145">Além disso, o módulo `BananaHelpers` e a classe `Banana` também fazer referência uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="cc474-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="cc474-146">Isso não seria possível expressar em F #, se você tiver removido o `rec` palavra-chave do `MutualReferences` namespace.</span><span class="sxs-lookup"><span data-stu-id="cc474-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="cc474-147">Esse recurso também está disponível para o nível superior [módulos](modules.md) em F # 4.1 ou superior.</span><span class="sxs-lookup"><span data-stu-id="cc474-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc474-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc474-148">See Also</span></span>
[<span data-ttu-id="cc474-149">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="cc474-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="cc474-150">Módulos</span><span class="sxs-lookup"><span data-stu-id="cc474-150">Modules</span></span>](modules.md)

[<span data-ttu-id="cc474-151">F # RFC FS-1009 - permitir tipos mutuamente referenciais e módulos em escopos maiores em arquivos</span><span class="sxs-lookup"><span data-stu-id="cc474-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)

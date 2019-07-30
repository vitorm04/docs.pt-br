---
title: Namespaces
description: Saiba como um F# namespace permite que você organize o código em áreas de funcionalidades relacionadas, permitindo que você anexe um nome a um agrupamento de elementos de programa.
ms.date: 12/08/2018
ms.openlocfilehash: d295f25cae81bc28b4fcb522bdcacde862f9517a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627383"
---
# <a name="namespaces"></a><span data-ttu-id="078c0-103">Namespaces</span><span class="sxs-lookup"><span data-stu-id="078c0-103">Namespaces</span></span>

<span data-ttu-id="078c0-104">Um namespace permite que você organize o código em áreas de funcionalidades relacionadas, permitindo que você anexe um nome a um F# agrupamento de elementos do programa.</span><span class="sxs-lookup"><span data-stu-id="078c0-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of F# program elements.</span></span> <span data-ttu-id="078c0-105">Os namespaces normalmente são elementos de nível superior F# em arquivos.</span><span class="sxs-lookup"><span data-stu-id="078c0-105">Namespaces are typically top-level elements in F# files.</span></span>

## <a name="syntax"></a><span data-ttu-id="078c0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="078c0-106">Syntax</span></span>

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="078c0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="078c0-107">Remarks</span></span>

<span data-ttu-id="078c0-108">Se você quiser colocar o código em um namespace, a primeira declaração no arquivo deverá declarar o namespace.</span><span class="sxs-lookup"><span data-stu-id="078c0-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="078c0-109">O conteúdo de todo o arquivo torna-se parte do namespace, desde que não exista mais nenhuma declaração de namespace no arquivo.</span><span class="sxs-lookup"><span data-stu-id="078c0-109">The contents of the entire file then become part of the namespace, provided no other namespaces declaration exists further in the file.</span></span> <span data-ttu-id="078c0-110">Se esse for o caso, então, todos os códigos até a próxima declaração de namespace serão considerados no primeiro namespace.</span><span class="sxs-lookup"><span data-stu-id="078c0-110">If that is the case, then all code up until the next namespace declaration is considered to be within the first namespace.</span></span>

<span data-ttu-id="078c0-111">Os namespaces não podem conter diretamente valores e funções.</span><span class="sxs-lookup"><span data-stu-id="078c0-111">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="078c0-112">Em vez disso, os valores e funções devem ser incluídos em módulos, e os módulos são incluídos em namespaces.</span><span class="sxs-lookup"><span data-stu-id="078c0-112">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="078c0-113">Namespaces podem conter tipos, módulos.</span><span class="sxs-lookup"><span data-stu-id="078c0-113">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="078c0-114">Comentários de documentos XML podem ser declarados acima de um namespace, mas são ignorados.</span><span class="sxs-lookup"><span data-stu-id="078c0-114">XML doc comments can be declared above a namespace, but they're ignored.</span></span> <span data-ttu-id="078c0-115">As diretivas do compilador também podem ser declaradas acima de um namespace.</span><span class="sxs-lookup"><span data-stu-id="078c0-115">Compiler directives can also be declared above a namespace.</span></span>

<span data-ttu-id="078c0-116">Os namespaces podem ser declarados explicitamente com a palavra-chave namespace ou implicitamente ao declarar um módulo.</span><span class="sxs-lookup"><span data-stu-id="078c0-116">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="078c0-117">Para declarar explicitamente um namespace, use a palavra-chave namespace seguida pelo nome do namespace.</span><span class="sxs-lookup"><span data-stu-id="078c0-117">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="078c0-118">O exemplo a seguir mostra um arquivo de código que declara um `Widgets` namespace com um tipo e um módulo incluídos nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="078c0-118">The following example shows a code file that declares a namespace `Widgets` with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="078c0-119">Se todo o conteúdo do arquivo estiver em um módulo, você também poderá declarar Namespaces implicitamente usando a `module` palavra-chave e fornecendo o novo nome de namespace no nome do módulo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="078c0-119">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="078c0-120">O exemplo a seguir mostra um arquivo de código que declara um `Widgets` namespace e um `WidgetsModule`módulo, que contém uma função.</span><span class="sxs-lookup"><span data-stu-id="078c0-120">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="078c0-121">O código a seguir é equivalente ao código anterior, mas o módulo é uma declaração de módulo local.</span><span class="sxs-lookup"><span data-stu-id="078c0-121">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="078c0-122">Nesse caso, o namespace deve aparecer em sua própria linha.</span><span class="sxs-lookup"><span data-stu-id="078c0-122">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="078c0-123">Se mais de um módulo for necessário no mesmo arquivo em um ou mais namespaces, você deverá usar declarações de módulo local.</span><span class="sxs-lookup"><span data-stu-id="078c0-123">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="078c0-124">Quando você usa declarações de módulo local, não pode usar o namespace qualificado nas declarações de módulo.</span><span class="sxs-lookup"><span data-stu-id="078c0-124">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="078c0-125">O código a seguir mostra um arquivo que tem uma declaração de namespace e duas declarações de módulo local.</span><span class="sxs-lookup"><span data-stu-id="078c0-125">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="078c0-126">Nesse caso, os módulos estão contidos diretamente no namespace; Não há um módulo criado implicitamente que tenha o mesmo nome que o arquivo.</span><span class="sxs-lookup"><span data-stu-id="078c0-126">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="078c0-127">Qualquer outro código no arquivo, como uma `do` associação, está no namespace, mas não nos módulos internos, portanto, você precisa qualificar o membro `widgetFunction` do módulo usando o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="078c0-127">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="078c0-128">A saída deste exemplo é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="078c0-128">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="078c0-129">Para obter mais informações, consulte [módulos](modules.md).</span><span class="sxs-lookup"><span data-stu-id="078c0-129">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="078c0-130">Namespaces aninhados</span><span class="sxs-lookup"><span data-stu-id="078c0-130">Nested Namespaces</span></span>

<span data-ttu-id="078c0-131">Ao criar um namespace aninhado, você deve qualificá-lo totalmente.</span><span class="sxs-lookup"><span data-stu-id="078c0-131">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="078c0-132">Caso contrário, você cria um novo namespace de nível superior.</span><span class="sxs-lookup"><span data-stu-id="078c0-132">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="078c0-133">O recuo é ignorado nas declarações de namespace.</span><span class="sxs-lookup"><span data-stu-id="078c0-133">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="078c0-134">O exemplo a seguir mostra como declarar um namespace aninhado.</span><span class="sxs-lookup"><span data-stu-id="078c0-134">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="078c0-135">Namespaces em arquivos e assemblies</span><span class="sxs-lookup"><span data-stu-id="078c0-135">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="078c0-136">Os namespaces podem abranger vários arquivos em um único projeto ou compilação.</span><span class="sxs-lookup"><span data-stu-id="078c0-136">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="078c0-137">O *fragmento do namespace* de termo descreve a parte de um namespace que está incluído em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="078c0-137">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="078c0-138">Os namespaces também podem abranger vários assemblies.</span><span class="sxs-lookup"><span data-stu-id="078c0-138">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="078c0-139">Por exemplo, o `System` namespace inclui a .NET Framework inteira, que abrange muitos assemblies e contém muitos namespaces aninhados.</span><span class="sxs-lookup"><span data-stu-id="078c0-139">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="078c0-140">Namespace global</span><span class="sxs-lookup"><span data-stu-id="078c0-140">Global Namespace</span></span>

<span data-ttu-id="078c0-141">Você usa o namespace `global` predefinido para colocar nomes no namespace de nível superior do .net.</span><span class="sxs-lookup"><span data-stu-id="078c0-141">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="078c0-142">Você também pode usar global para fazer referência ao namespace .NET de nível superior, por exemplo, para resolver conflitos de nome com outros namespaces.</span><span class="sxs-lookup"><span data-stu-id="078c0-142">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="078c0-143">Namespaces recursivos</span><span class="sxs-lookup"><span data-stu-id="078c0-143">Recursive namespaces</span></span>

<span data-ttu-id="078c0-144">Os namespaces também podem ser declarados como recursivos para permitir que todo o código independente seja recursivo mutuamente.</span><span class="sxs-lookup"><span data-stu-id="078c0-144">Namespaces can also be declared as recursive to allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="078c0-145">Isso é feito por `namespace rec`meio de.</span><span class="sxs-lookup"><span data-stu-id="078c0-145">This is done via `namespace rec`.</span></span> <span data-ttu-id="078c0-146">O uso `namespace rec` de pode aliviar alguns problemas em não ser capaz de escrever código referencial mutuamente entre tipos e módulos.</span><span class="sxs-lookup"><span data-stu-id="078c0-146">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span> <span data-ttu-id="078c0-147">Veja a seguir um exemplo disso:</span><span class="sxs-lookup"><span data-stu-id="078c0-147">The following is an example of this:</span></span>

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
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="078c0-148">Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` fazem referência umas às outras.</span><span class="sxs-lookup"><span data-stu-id="078c0-148">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="078c0-149">Além disso, o `BananaHelpers` módulo e a `Banana` classe também se referem uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="078c0-149">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span> <span data-ttu-id="078c0-150">Isso não seria possível expressar em F# se você removesse a `rec` palavra-chave do `MutualReferences` namespace.</span><span class="sxs-lookup"><span data-stu-id="078c0-150">This wouldn't be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="078c0-151">Esse recurso também está disponível para [módulos](modules.md)de nível superior.</span><span class="sxs-lookup"><span data-stu-id="078c0-151">This feature is also available for top-level [Modules](modules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="078c0-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="078c0-152">See also</span></span>

- [<span data-ttu-id="078c0-153">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="078c0-153">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="078c0-154">Módulos</span><span class="sxs-lookup"><span data-stu-id="078c0-154">Modules</span></span>](modules.md)
- [<span data-ttu-id="078c0-155">F#RFC FS-1009-permitir tipos e módulos de referência mútua em escopos maiores nos arquivos</span><span class="sxs-lookup"><span data-stu-id="078c0-155">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)

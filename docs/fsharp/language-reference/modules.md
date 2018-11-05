---
title: Módulos (F#)
description: 'Saiba como um módulo do F # é um agrupamento de código F #, como valores, tipos e valores de função em um programa em F #.'
ms.date: 04/24/2017
ms.openlocfilehash: fb0aa1d508d1141933b4fbdf10633f67ed078dc7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45528520"
---
# <a name="modules"></a><span data-ttu-id="4e7f7-103">Módulos</span><span class="sxs-lookup"><span data-stu-id="4e7f7-103">Modules</span></span>

<span data-ttu-id="4e7f7-104">No contexto da linguagem F #, uma *módulo* é um agrupamento de código F #, como valores, tipos e valores de função em um programa em F #.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="4e7f7-105">O agrupamento de código em módulos ajuda a manter junto o código relacionado e ajuda a evitar conflitos de nome em seu programa.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e7f7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e7f7-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="4e7f7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4e7f7-107">Remarks</span></span>

<span data-ttu-id="4e7f7-108">Um módulo do F # é um agrupamento de construções de código F #, como tipos, valores, valores de função e código em `do` associações.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="4e7f7-109">Ele é implementado como uma classe de runtime (CLR) de linguagem comum que tem apenas membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="4e7f7-110">Há dois tipos de declarações de módulo, dependendo se o arquivo inteiro é incluído no módulo: uma declaração de módulo de nível superior e uma declaração de módulo local.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="4e7f7-111">Uma declaração de módulo de nível superior inclui todo o arquivo no módulo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="4e7f7-112">Uma declaração de módulo de nível superior pode aparecer somente como a primeira declaração em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="4e7f7-113">Na sintaxe para a declaração de módulo de nível superior, opcional *namespace qualificado* é a sequência de nomes de namespace aninhado que contém o módulo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="4e7f7-114">O namespace qualificado não precisa ser declarado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="4e7f7-115">Não é preciso recuar as declarações em um módulo de nível superior.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="4e7f7-116">Você tem que recuar todas as declarações em módulos de locais.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="4e7f7-117">Em uma declaração de módulo local, somente as declarações são recuadas sob essa declaração de módulo são parte do módulo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="4e7f7-118">Se um arquivo de código não começa com uma declaração de módulo de nível superior ou uma declaração de namespace, todo o conteúdo do arquivo, incluindo todos os módulos locais, torna-se parte de um módulo de nível superior criado implicitamente que tem o mesmo nome do arquivo, sem a extensão com a primeira letra convertida em maiusculas.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="4e7f7-119">Por exemplo, considere o seguinte arquivo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="4e7f7-120">Esse arquivo deve ser compilado como se tivesse sido escrito desta forma:</span><span class="sxs-lookup"><span data-stu-id="4e7f7-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="4e7f7-121">Se você tiver vários módulos em um arquivo, você deve usar uma declaração de módulo local para cada módulo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="4e7f7-122">Se um namespace delimitador for declarado, esses módulos são parte do namespace delimitador.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="4e7f7-123">Se um namespace delimitador não for declarado, os módulos se tornam parte do módulo de nível superior criado implicitamente.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="4e7f7-124">O exemplo de código a seguir mostra um arquivo de código que contém vários módulos.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="4e7f7-125">O compilador cria implicitamente um módulo de nível superior chamado `Multiplemodules`, e `MyModule1` e `MyModule2` estão aninhados em desse módulo de nível superior.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="4e7f7-126">Se você tiver vários arquivos em um projeto ou em uma única compilação, ou se você estiver criando uma biblioteca, você deve incluir uma declaração de namespace ou a declaração de módulo na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="4e7f7-127">O compilador F # determina apenas um nome de módulo em implicitamente quando há apenas um arquivo em uma linha de comando de compilação ou de projeto, e você estiver criando um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="4e7f7-128">O *modificador de acessibilidade* pode ser uma das seguintes opções: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="4e7f7-129">Para saber mais, veja [Controle de acesso](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="4e7f7-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="4e7f7-130">O padrão é público.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="4e7f7-131">Código de referência em módulos</span><span class="sxs-lookup"><span data-stu-id="4e7f7-131">Referencing Code in Modules</span></span>

<span data-ttu-id="4e7f7-132">Quando você faz referência a funções, tipos e valores de outro módulo, você deve usar um nome qualificado ou abra o módulo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="4e7f7-133">Se você usar um nome qualificado, você deve especificar os namespaces, o módulo e o identificador para o elemento de programa que você deseja.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="4e7f7-134">Separe cada parte do caminho qualificado com um ponto (.), da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="4e7f7-135">Você pode abrir o módulo ou um ou mais namespaces para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="4e7f7-136">Para obter mais informações sobre namespaces de abertura e de módulos, consulte [declarações de importação: A `open` palavra-chave](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="4e7f7-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="4e7f7-137">O exemplo de código a seguir mostra um módulo de nível superior que contém todo o código até o final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="4e7f7-138">Para usar esse código de outro arquivo no mesmo projeto, você usar nomes qualificados ou abra o módulo antes de usar as funções, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="4e7f7-139">Módulos aninhados</span><span class="sxs-lookup"><span data-stu-id="4e7f7-139">Nested Modules</span></span>

<span data-ttu-id="4e7f7-140">Os módulos podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-140">Modules can be nested.</span></span> <span data-ttu-id="4e7f7-141">Módulos internos devem ser recuados com relação às General declarações de módulo externo para indicar que são módulos internos, não novos módulos.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="4e7f7-142">Por exemplo, compare os dois exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-142">For example, compare the following two examples.</span></span> <span data-ttu-id="4e7f7-143">Módulo `Z` é um módulo interno no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="4e7f7-144">Mas o módulo `Z` for um irmão para o módulo `Y` no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="4e7f7-145">Módulo `Z` também é um módulo de irmão no código a seguir, porque ele não é recuado com relação às General outras declarações de módulo `Y`.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="4e7f7-146">Por fim, se o módulo externo não tem nenhuma declaração e é seguido imediatamente por outra declaração de módulo, a nova declaração de módulo é considerada como um módulo interno, mas o compilador avisará se a segunda definição de módulo não ficará recuada mais além do que o primeiro.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="4e7f7-147">Para eliminar o aviso, recue o módulo interno.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="4e7f7-148">Se desejar que todo o código em um arquivo em um único módulo externo e você desejar módulos internos, o módulo externo não exige que o sinal de igual, e as declarações, incluindo qualquer declaração de módulo interno, que entrarão no módulo externo não precisam ser recuado.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="4e7f7-149">As declarações dentro de declarações de módulo interno precisa ser recuada.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="4e7f7-150">O código a seguir mostra esse caso.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-150">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="4e7f7-151">Módulos de recursiva</span><span class="sxs-lookup"><span data-stu-id="4e7f7-151">Recursive modules</span></span>

<span data-ttu-id="4e7f7-152">F # 4.1 introduz a noção de módulos que permitem para todo o código contido ser mutuamente recursivas.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="4e7f7-153">Isso é feito por meio de `module rec`.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-153">This is done via `module rec`.</span></span>  <span data-ttu-id="4e7f7-154">Uso de `module rec` podem aliviar alguns problemas ao não ser capaz de escrever código mutuamente referencial entre módulos e tipos.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="4e7f7-155">Este é um exemplo disso:</span><span class="sxs-lookup"><span data-stu-id="4e7f7-155">The following is an example of this:</span></span>

```fsharp
module rec RecursiveModule =
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

<span data-ttu-id="4e7f7-156">Observe que a exceção `DontSqueezeTheBananaException` e a classe `Banana` fazem referência entre si.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="4e7f7-157">Além disso, o módulo `BananaHelpers` e a classe `Banana` também fazer referência uns aos outros.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="4e7f7-158">Isso não seria possível expressar em F #, se você tiver removido o `rec` palavra-chave do `RecursiveModule` módulo.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="4e7f7-159">Esse recurso também é possível no [Namespaces](namespaces.md) com F # 4.1.</span><span class="sxs-lookup"><span data-stu-id="4e7f7-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e7f7-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e7f7-160">See also</span></span>

- [<span data-ttu-id="4e7f7-161">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4e7f7-161">F# Language Reference</span></span>](index.md)  
- [<span data-ttu-id="4e7f7-162">Namespaces</span><span class="sxs-lookup"><span data-stu-id="4e7f7-162">Namespaces</span></span>](namespaces.md)  
- [<span data-ttu-id="4e7f7-163">FS-1009 do F # RFC - permitir mutuamente referenciais tipos e módulos em escopos maiores dentro de arquivos</span><span class="sxs-lookup"><span data-stu-id="4e7f7-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  

---
title: 'Declarações de importação: a palavra-chave open'
description: 'Saiba mais sobre as declarações de importação de F # e como elas especificam um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.'
ms.date: 08/15/2020
ms.openlocfilehash: ab208c53809e120bc216c8f8b4d04a322d67cf2f
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557175"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="03735-103">Importar declarações: a `open` palavra-chave</span><span class="sxs-lookup"><span data-stu-id="03735-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="03735-104">Uma *declaração de importação* especifica um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="03735-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="03735-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03735-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
open type type-name
```

## <a name="remarks"></a><span data-ttu-id="03735-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="03735-106">Remarks</span></span>

<span data-ttu-id="03735-107">Fazer referência ao código usando o namespace totalmente qualificado ou o caminho do módulo toda vez pode criar código que seja difícil de gravar, ler e manter.</span><span class="sxs-lookup"><span data-stu-id="03735-107">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="03735-108">Em vez disso, você pode usar a `open` palavra-chave para módulos e namespaces usados com frequência para que, ao fazer referência a um membro desse módulo ou namespace, você possa usar a forma abreviada do nome em vez do nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="03735-108">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="03735-109">Essa palavra-chave é semelhante à `using` palavra-chave em C#, `using namespace` em Visual C++ e `Imports` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03735-109">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="03735-110">O módulo ou namespace fornecido deve estar no mesmo projeto ou em um projeto ou assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="03735-110">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="03735-111">Se não estiver, você poderá adicionar uma referência ao projeto ou usar a `-reference` opção de linha de comando (ou sua abreviação, `-r` ).</span><span class="sxs-lookup"><span data-stu-id="03735-111">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="03735-112">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="03735-112">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="03735-113">A declaração de importação torna os nomes disponíveis no código que segue a declaração, até o final do namespace, módulo ou arquivo de circunscrição.</span><span class="sxs-lookup"><span data-stu-id="03735-113">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="03735-114">Quando você usa várias declarações de importação, elas devem aparecer em linhas separadas.</span><span class="sxs-lookup"><span data-stu-id="03735-114">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="03735-115">O código a seguir mostra o uso da `open` palavra-chave para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="03735-115">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="03735-116">O compilador F # não emite um erro ou aviso quando as ambiguidades ocorrem quando o mesmo nome ocorre em mais de um módulo ou namespace aberto.</span><span class="sxs-lookup"><span data-stu-id="03735-116">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="03735-117">Quando ocorrerem ambiguidades, F # dará preferência ao módulo ou namespace mais recentemente aberto.</span><span class="sxs-lookup"><span data-stu-id="03735-117">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="03735-118">Por exemplo, no código a seguir, `empty` significa `Seq.empty` , embora `empty` esteja localizado nos `List` `Seq` módulos e.</span><span class="sxs-lookup"><span data-stu-id="03735-118">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="03735-119">Portanto, tenha cuidado ao abrir módulos ou namespaces, como `List` ou `Seq` que contenham Membros com nomes idênticos; em vez disso, considere usar os nomes qualificados.</span><span class="sxs-lookup"><span data-stu-id="03735-119">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="03735-120">Você deve evitar qualquer situação na qual o código seja dependente da ordem das declarações de importação.</span><span class="sxs-lookup"><span data-stu-id="03735-120">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="03735-121">Abrir declarações de tipo</span><span class="sxs-lookup"><span data-stu-id="03735-121">Open type declarations</span></span>

<span data-ttu-id="03735-122">O F # dá suporte `open` a um tipo como este:</span><span class="sxs-lookup"><span data-stu-id="03735-122">F# supports `open` on a type like so:</span></span>

```fsharp
open type System.Math
PI
```

<span data-ttu-id="03735-123">Isso vai expor todos os campos estáticos e membros acessíveis no tipo.</span><span class="sxs-lookup"><span data-stu-id="03735-123">This will expose all accessible static fields and members on the type.</span></span>

<span data-ttu-id="03735-124">Você também pode `open` [gravar registros](records.md) definidos e tipos de [União discriminados](discriminated-unions.md) em F # para expor membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="03735-124">You can also `open` F#-defined [record](records.md) and [discriminated union](discriminated-unions.md) types to expose static members.</span></span> <span data-ttu-id="03735-125">No caso de uniões discriminadas, você também pode expor os casos de União.</span><span class="sxs-lookup"><span data-stu-id="03735-125">In the case of discriminated unions, you can also expose the union cases.</span></span> <span data-ttu-id="03735-126">Isso pode ser útil para acessar casos de União em um tipo declarado dentro de um módulo que talvez você não queira abrir, desta forma:</span><span class="sxs-lookup"><span data-stu-id="03735-126">This can be helpful for accessing union cases in a type declared inside of a module that you may not want to open, like so:</span></span>

```fsharp
module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="03735-127">Namespaces que estão abertos por padrão</span><span class="sxs-lookup"><span data-stu-id="03735-127">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="03735-128">Alguns namespaces são frequentemente usados no código F # que eles são abertos implicitamente sem a necessidade de uma declaração de importação explícita.</span><span class="sxs-lookup"><span data-stu-id="03735-128">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="03735-129">A tabela a seguir mostra os namespaces que estão abertos por padrão.</span><span class="sxs-lookup"><span data-stu-id="03735-129">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="03735-130">Namespace</span><span class="sxs-lookup"><span data-stu-id="03735-130">Namespace</span></span>|<span data-ttu-id="03735-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="03735-131">Description</span></span>|
|---------|-----------|
|`FSharp.Core`|<span data-ttu-id="03735-132">Contém definições de tipo F # básicas para tipos internos, como `int` e `float` .</span><span class="sxs-lookup"><span data-stu-id="03735-132">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`FSharp.Core.Operators`|<span data-ttu-id="03735-133">Contém operações aritméticas básicas, como `+` e `*` .</span><span class="sxs-lookup"><span data-stu-id="03735-133">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`FSharp.Collections`|<span data-ttu-id="03735-134">Contém classes de coleção imutáveis, como `List` e `Array` .</span><span class="sxs-lookup"><span data-stu-id="03735-134">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`FSharp.Control`|<span data-ttu-id="03735-135">Contém tipos de construções de controle, como avaliação lenta e fluxos de trabalho assíncronos.</span><span class="sxs-lookup"><span data-stu-id="03735-135">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`FSharp.Text`|<span data-ttu-id="03735-136">Contém funções para e/s formatada, como a `printf` função.</span><span class="sxs-lookup"><span data-stu-id="03735-136">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="03735-137">Atributo AutoOpen</span><span class="sxs-lookup"><span data-stu-id="03735-137">AutoOpen Attribute</span></span>

<span data-ttu-id="03735-138">Você pode aplicar o `AutoOpen` atributo a um assembly se desejar abrir automaticamente um namespace ou módulo quando o assembly for referenciado.</span><span class="sxs-lookup"><span data-stu-id="03735-138">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="03735-139">Você também pode aplicar o `AutoOpen` atributo a um módulo para abrir esse módulo automaticamente quando o namespace ou o módulo pai for aberto.</span><span class="sxs-lookup"><span data-stu-id="03735-139">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="03735-140">Para obter mais informações, consulte [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span><span class="sxs-lookup"><span data-stu-id="03735-140">For more information, see [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="03735-141">Atributo RequireQualifiedAccess</span><span class="sxs-lookup"><span data-stu-id="03735-141">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="03735-142">Alguns módulos, registros ou tipos de União podem especificar o `RequireQualifiedAccess` atributo.</span><span class="sxs-lookup"><span data-stu-id="03735-142">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="03735-143">Ao referenciar elementos desses módulos, registros ou uniões, você deve usar um nome qualificado, independentemente de você incluir uma declaração de importação.</span><span class="sxs-lookup"><span data-stu-id="03735-143">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="03735-144">Se você usar esse atributo estrategicamente em tipos que definem nomes comumente usados, você ajudará a evitar colisões de nomes e, portanto, tornará o código mais resiliente às alterações nas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="03735-144">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="03735-145">Para obter mais informações, consulte [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span><span class="sxs-lookup"><span data-stu-id="03735-145">For more information, see [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="03735-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03735-146">See also</span></span>

- [<span data-ttu-id="03735-147">Referência de linguagem F #</span><span class="sxs-lookup"><span data-stu-id="03735-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="03735-148">Namespaces</span><span class="sxs-lookup"><span data-stu-id="03735-148">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="03735-149">Módulos</span><span class="sxs-lookup"><span data-stu-id="03735-149">Modules</span></span>](modules.md)

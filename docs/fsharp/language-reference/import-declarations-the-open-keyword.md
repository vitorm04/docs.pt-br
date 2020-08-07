---
title: 'Declarações de importação: a palavra-chave open'
description: 'Saiba mais sobre as declarações de importação de F # e como elas especificam um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.'
ms.date: 04/04/2019
ms.openlocfilehash: 2b88427ca92212fb4a7598447dd1a5e12061093a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855082"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="431cf-103">Importar declarações: a `open` palavra-chave</span><span class="sxs-lookup"><span data-stu-id="431cf-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="431cf-104">Uma *declaração de importação* especifica um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="431cf-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="431cf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="431cf-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="431cf-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="431cf-106">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="431cf-107">A referência da API docs.microsoft.com para F # não está completa.</span><span class="sxs-lookup"><span data-stu-id="431cf-107">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="431cf-108">Se você encontrar links desfeitos, consulte a [documentação da biblioteca principal F #](https://fsharp.github.io/fsharp-core-docs/) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="431cf-108">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

<span data-ttu-id="431cf-109">Fazer referência ao código usando o namespace totalmente qualificado ou o caminho do módulo toda vez pode criar código que seja difícil de gravar, ler e manter.</span><span class="sxs-lookup"><span data-stu-id="431cf-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="431cf-110">Em vez disso, você pode usar a `open` palavra-chave para módulos e namespaces usados com frequência para que, ao fazer referência a um membro desse módulo ou namespace, você possa usar a forma abreviada do nome em vez do nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="431cf-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="431cf-111">Essa palavra-chave é semelhante à `using` palavra-chave em C#, `using namespace` em Visual C++ e `Imports` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="431cf-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="431cf-112">O módulo ou namespace fornecido deve estar no mesmo projeto ou em um projeto ou assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="431cf-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="431cf-113">Se não estiver, você poderá adicionar uma referência ao projeto ou usar a `-reference` opção de linha de comando (ou sua abreviação, `-r` ).</span><span class="sxs-lookup"><span data-stu-id="431cf-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="431cf-114">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="431cf-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="431cf-115">A declaração de importação torna os nomes disponíveis no código que segue a declaração, até o final do namespace, módulo ou arquivo de circunscrição.</span><span class="sxs-lookup"><span data-stu-id="431cf-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="431cf-116">Quando você usa várias declarações de importação, elas devem aparecer em linhas separadas.</span><span class="sxs-lookup"><span data-stu-id="431cf-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="431cf-117">O código a seguir mostra o uso da `open` palavra-chave para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="431cf-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="431cf-118">O compilador F # não emite um erro ou aviso quando as ambiguidades ocorrem quando o mesmo nome ocorre em mais de um módulo ou namespace aberto.</span><span class="sxs-lookup"><span data-stu-id="431cf-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="431cf-119">Quando ocorrerem ambiguidades, F # dará preferência ao módulo ou namespace mais recentemente aberto.</span><span class="sxs-lookup"><span data-stu-id="431cf-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="431cf-120">Por exemplo, no código a seguir, `empty` significa `Seq.empty` , embora `empty` esteja localizado nos `List` `Seq` módulos e.</span><span class="sxs-lookup"><span data-stu-id="431cf-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="431cf-121">Portanto, tenha cuidado ao abrir módulos ou namespaces, como `List` ou `Seq` que contenham Membros com nomes idênticos; em vez disso, considere usar os nomes qualificados.</span><span class="sxs-lookup"><span data-stu-id="431cf-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="431cf-122">Você deve evitar qualquer situação na qual o código seja dependente da ordem das declarações de importação.</span><span class="sxs-lookup"><span data-stu-id="431cf-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="431cf-123">Namespaces que estão abertos por padrão</span><span class="sxs-lookup"><span data-stu-id="431cf-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="431cf-124">Alguns namespaces são frequentemente usados no código F # que eles são abertos implicitamente sem a necessidade de uma declaração de importação explícita.</span><span class="sxs-lookup"><span data-stu-id="431cf-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="431cf-125">A tabela a seguir mostra os namespaces que estão abertos por padrão.</span><span class="sxs-lookup"><span data-stu-id="431cf-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="431cf-126">Namespace</span><span class="sxs-lookup"><span data-stu-id="431cf-126">Namespace</span></span>|<span data-ttu-id="431cf-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="431cf-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="431cf-128">Contém definições de tipo F # básicas para tipos internos, como `int` e `float` .</span><span class="sxs-lookup"><span data-stu-id="431cf-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="431cf-129">Contém operações aritméticas básicas, como `+` e `*` .</span><span class="sxs-lookup"><span data-stu-id="431cf-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="431cf-130">Contém classes de coleção imutáveis, como `List` e `Array` .</span><span class="sxs-lookup"><span data-stu-id="431cf-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="431cf-131">Contém tipos de construções de controle, como avaliação lenta e fluxos de trabalho assíncronos.</span><span class="sxs-lookup"><span data-stu-id="431cf-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="431cf-132">Contém funções para e/s formatada, como a `printf` função.</span><span class="sxs-lookup"><span data-stu-id="431cf-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="431cf-133">Atributo AutoOpen</span><span class="sxs-lookup"><span data-stu-id="431cf-133">AutoOpen Attribute</span></span>

<span data-ttu-id="431cf-134">Você pode aplicar o `AutoOpen` atributo a um assembly se desejar abrir automaticamente um namespace ou módulo quando o assembly for referenciado.</span><span class="sxs-lookup"><span data-stu-id="431cf-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="431cf-135">Você também pode aplicar o `AutoOpen` atributo a um módulo para abrir esse módulo automaticamente quando o namespace ou o módulo pai for aberto.</span><span class="sxs-lookup"><span data-stu-id="431cf-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="431cf-136">Para obter mais informações, consulte [classe Core. AutoOpenAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="431cf-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="431cf-137">Atributo RequireQualifiedAccess</span><span class="sxs-lookup"><span data-stu-id="431cf-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="431cf-138">Alguns módulos, registros ou tipos de União podem especificar o `RequireQualifiedAccess` atributo.</span><span class="sxs-lookup"><span data-stu-id="431cf-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="431cf-139">Ao referenciar elementos desses módulos, registros ou uniões, você deve usar um nome qualificado, independentemente de você incluir uma declaração de importação.</span><span class="sxs-lookup"><span data-stu-id="431cf-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="431cf-140">Se você usar esse atributo estrategicamente em tipos que definem nomes comumente usados, você ajudará a evitar colisões de nomes e, portanto, tornará o código mais resiliente às alterações nas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="431cf-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="431cf-141">Para obter mais informações, consulte [classe Core. RequireQualifiedAccessAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="431cf-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="431cf-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="431cf-142">See also</span></span>

- [<span data-ttu-id="431cf-143">Referência de linguagem F #</span><span class="sxs-lookup"><span data-stu-id="431cf-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="431cf-144">Namespaces</span><span class="sxs-lookup"><span data-stu-id="431cf-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="431cf-145">Módulos</span><span class="sxs-lookup"><span data-stu-id="431cf-145">Modules</span></span>](modules.md)

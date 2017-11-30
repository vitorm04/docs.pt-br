---
title: "Declarações de importação: a palavra-chave open (F#)"
description: "Saiba mais sobre declarações de importação do F # e como elas especificam um módulo ou namespace cujos elementos que você pode fazer referência sem usar um nome totalmente qualificado."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1e98e48c-52e9-4314-8954-85d5583125f0
ms.openlocfilehash: a6d79bed3dd202657d06956edf9499a9b21a5f03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="670bf-104">Declarações de importação: O `open` palavra-chave</span><span class="sxs-lookup"><span data-stu-id="670bf-104">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="670bf-105">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="670bf-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="670bf-106">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="670bf-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="670bf-107">Um *declaração da importação* Especifica um módulo ou namespace cujos elementos que você pode fazer referência sem usar um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="670bf-107">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>


## <a name="syntax"></a><span data-ttu-id="670bf-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="670bf-108">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="670bf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="670bf-109">Remarks</span></span>
<span data-ttu-id="670bf-110">Referência de código usando o caminho totalmente qualificado de namespace ou módulo sempre pode criar o código que é difícil de gravar, ler e manter.</span><span class="sxs-lookup"><span data-stu-id="670bf-110">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="670bf-111">Em vez disso, você pode usar o `open` palavra-chave usados em módulos e namespaces para que quando você faz referência a um membro desse módulo ou namespace, você pode usar a forma abreviada do nome em vez do nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="670bf-111">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="670bf-112">Esta palavra-chave é semelhante do `using` palavra-chave em c#, `using namespace` no Visual C++, e `Imports` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="670bf-112">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="670bf-113">O módulo ou namespace fornecido deve ser no mesmo projeto ou em um projeto referenciado ou assembly.</span><span class="sxs-lookup"><span data-stu-id="670bf-113">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="670bf-114">Se não estiver, você pode adicionar uma referência ao projeto ou usar o `-reference` comando`-`opção de linha (ou abreviatura, `-r`).</span><span class="sxs-lookup"><span data-stu-id="670bf-114">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="670bf-115">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="670bf-115">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="670bf-116">A declaração de importação disponibiliza os nomes no código que segue a declaração, até o fim do delimitador namespace, módulo ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="670bf-116">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="670bf-117">Quando você usa várias declarações de importação, devem ser exibidos em linhas separadas.</span><span class="sxs-lookup"><span data-stu-id="670bf-117">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="670bf-118">O código a seguir mostra o uso do `open` palavra-chave para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="670bf-118">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="670bf-119">O compilador F # não emite um erro ou aviso quando ambiguidades ocorrem quando ocorre o mesmo nome em mais de um namespace ou módulo aberto.</span><span class="sxs-lookup"><span data-stu-id="670bf-119">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="670bf-120">Quando ambiguidades ocorrem, F # dá preferência para o namespace ou módulo abertas mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="670bf-120">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="670bf-121">Por exemplo, no código a seguir, `empty` significa `Seq.empty`, mesmo que `empty` está localizado em ambos os `List` e `Seq` módulos.</span><span class="sxs-lookup"><span data-stu-id="670bf-121">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="670bf-122">Portanto, tenha cuidado ao abrir módulos ou namespaces, como `List` ou `Seq` que contêm membros que tenham nomes idênticos; em vez disso, considere usar os nomes qualificados.</span><span class="sxs-lookup"><span data-stu-id="670bf-122">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="670bf-123">Você deve evitar qualquer situação em que o código é dependente de ordem das declarações de importação.</span><span class="sxs-lookup"><span data-stu-id="670bf-123">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>


## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="670bf-124">Namespaces que estão abertos por padrão</span><span class="sxs-lookup"><span data-stu-id="670bf-124">Namespaces That Are Open by Default</span></span>
<span data-ttu-id="670bf-125">Alguns namespaces são então usados no código F # que são abertas implicitamente sem a necessidade de uma declaração de importação explícita.</span><span class="sxs-lookup"><span data-stu-id="670bf-125">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="670bf-126">A tabela a seguir mostra os namespaces que estão abertos por padrão.</span><span class="sxs-lookup"><span data-stu-id="670bf-126">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="670bf-127">Namespace</span><span class="sxs-lookup"><span data-stu-id="670bf-127">Namespace</span></span>|<span data-ttu-id="670bf-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="670bf-128">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="670bf-129">Contém básicas definições de tipo F # para tipos internos, como `int` e `float`.</span><span class="sxs-lookup"><span data-stu-id="670bf-129">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="670bf-130">Contém operações aritméticas básicas como `+` e `*`.</span><span class="sxs-lookup"><span data-stu-id="670bf-130">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="670bf-131">Contém classes de coleção imutável como `List` e `Array`.</span><span class="sxs-lookup"><span data-stu-id="670bf-131">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="670bf-132">Contém tipos para construções de controle, como avaliação lenta e fluxos de trabalho assíncronos.</span><span class="sxs-lookup"><span data-stu-id="670bf-132">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="670bf-133">Contém funções de e/s formatado, tais como o `printf` função.</span><span class="sxs-lookup"><span data-stu-id="670bf-133">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="670bf-134">Atributo AutoOpen</span><span class="sxs-lookup"><span data-stu-id="670bf-134">AutoOpen Attribute</span></span>
<span data-ttu-id="670bf-135">Você pode aplicar o `AutoOpen` atributo a um assembly, se você quiser abrir automaticamente um namespace ou módulo quando o assembly é referenciado.</span><span class="sxs-lookup"><span data-stu-id="670bf-135">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="670bf-136">Você também pode aplicar o `AutoOpen` de atributo para um módulo para abrir o módulo automaticamente quando o módulo principal ou o namespace é aberto.</span><span class="sxs-lookup"><span data-stu-id="670bf-136">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="670bf-137">Para obter mais informações, consulte [classe autoopenattribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="670bf-137">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>


## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="670bf-138">Atributo RequireQualifiedAccess</span><span class="sxs-lookup"><span data-stu-id="670bf-138">RequireQualifiedAccess Attribute</span></span>
<span data-ttu-id="670bf-139">Alguns módulos, registros ou tipos de união podem especificar o `RequireQualifiedAccess` atributo.</span><span class="sxs-lookup"><span data-stu-id="670bf-139">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="670bf-140">Ao fazer referência a elementos desses módulos, registros ou uniões, você deve usar um nome qualificado, independentemente de se você incluir uma declaração de importação.</span><span class="sxs-lookup"><span data-stu-id="670bf-140">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="670bf-141">Se você usar esse atributo estrategicamente em nomes de tipos que definem comumente usados, ajudar a evitar conflitos de nome e, portanto, tornar o código mais resiliente a alterações em bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="670bf-141">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="670bf-142">Para obter mais informações, consulte [classe requirequalifiedaccessattribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="670bf-142">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>


## <a name="see-also"></a><span data-ttu-id="670bf-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="670bf-143">See Also</span></span>
[<span data-ttu-id="670bf-144"># Referência de linguagem</span><span class="sxs-lookup"><span data-stu-id="670bf-144"># Language Reference</span></span>](index.md)

[<span data-ttu-id="670bf-145">Namespaces</span><span class="sxs-lookup"><span data-stu-id="670bf-145">Namespaces</span></span>](namespaces.md)

[<span data-ttu-id="670bf-146">Módulos</span><span class="sxs-lookup"><span data-stu-id="670bf-146">Modules</span></span>](modules.md)


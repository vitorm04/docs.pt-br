---
title: 'Declarações de importação: A palavra-chave open'
description: Saiba mais F# sobre as declarações de importação e como elas especificam um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630579"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="c8b27-103">Declarações de importação: A palavra-chave `open`</span><span class="sxs-lookup"><span data-stu-id="c8b27-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="c8b27-104">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="c8b27-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="c8b27-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="c8b27-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="c8b27-106">Uma *declaração de importação* especifica um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="c8b27-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8b27-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8b27-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="c8b27-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8b27-108">Remarks</span></span>

<span data-ttu-id="c8b27-109">Fazer referência ao código usando o namespace totalmente qualificado ou o caminho do módulo toda vez pode criar código que seja difícil de gravar, ler e manter.</span><span class="sxs-lookup"><span data-stu-id="c8b27-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="c8b27-110">Em vez disso, você pode `open` usar a palavra-chave para módulos e namespaces usados com frequência para que, ao fazer referência a um membro desse módulo ou namespace, você possa usar a forma abreviada do nome em vez do nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="c8b27-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="c8b27-111">Essa palavra-chave é semelhante `using` à palavra C#- `using namespace` chave no C++, no `Imports` visual e no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8b27-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="c8b27-112">O módulo ou namespace fornecido deve estar no mesmo projeto ou em um projeto ou assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="c8b27-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="c8b27-113">Se não for, você poderá adicionar uma referência ao projeto ou usar a opção de linha `-reference` de`-`comando (ou sua abreviação, `-r`).</span><span class="sxs-lookup"><span data-stu-id="c8b27-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="c8b27-114">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="c8b27-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="c8b27-115">A declaração de importação torna os nomes disponíveis no código que segue a declaração, até o final do namespace, módulo ou arquivo de circunscrição.</span><span class="sxs-lookup"><span data-stu-id="c8b27-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="c8b27-116">Quando você usa várias declarações de importação, elas devem aparecer em linhas separadas.</span><span class="sxs-lookup"><span data-stu-id="c8b27-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="c8b27-117">O código a seguir mostra o uso da `open` palavra-chave para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="c8b27-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="c8b27-118">O F# compilador não emite um erro ou aviso quando as ambiguidades ocorrem quando o mesmo nome ocorre em mais de um módulo ou namespace aberto.</span><span class="sxs-lookup"><span data-stu-id="c8b27-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="c8b27-119">Quando ocorrerem ambiguidades F# , o fornecerá preferência para o módulo ou namespace aberto mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="c8b27-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="c8b27-120">Por exemplo, no código a seguir, `empty` significa `Seq.empty`, embora `empty` esteja localizado nos `List` módulos e `Seq` .</span><span class="sxs-lookup"><span data-stu-id="c8b27-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="c8b27-121">Portanto, tenha cuidado ao abrir módulos ou namespaces, `List` como ou `Seq` que contenham Membros com nomes idênticos; em vez disso, considere usar os nomes qualificados.</span><span class="sxs-lookup"><span data-stu-id="c8b27-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="c8b27-122">Você deve evitar qualquer situação na qual o código seja dependente da ordem das declarações de importação.</span><span class="sxs-lookup"><span data-stu-id="c8b27-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="c8b27-123">Namespaces que estão abertos por padrão</span><span class="sxs-lookup"><span data-stu-id="c8b27-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="c8b27-124">Alguns namespaces são tão frequentemente usados no F# código que são abertos implicitamente sem a necessidade de uma declaração de importação explícita.</span><span class="sxs-lookup"><span data-stu-id="c8b27-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="c8b27-125">A tabela a seguir mostra os namespaces que estão abertos por padrão.</span><span class="sxs-lookup"><span data-stu-id="c8b27-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="c8b27-126">Namespace</span><span class="sxs-lookup"><span data-stu-id="c8b27-126">Namespace</span></span>|<span data-ttu-id="c8b27-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8b27-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="c8b27-128">Contém definições F# de tipo básicas para tipos internos, `int` como e. `float`</span><span class="sxs-lookup"><span data-stu-id="c8b27-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="c8b27-129">Contém operações aritméticas básicas, `+` como `*`e.</span><span class="sxs-lookup"><span data-stu-id="c8b27-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="c8b27-130">Contém classes de coleção imutáveis, como `List` e `Array`.</span><span class="sxs-lookup"><span data-stu-id="c8b27-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="c8b27-131">Contém tipos de construções de controle, como avaliação lenta e fluxos de trabalho assíncronos.</span><span class="sxs-lookup"><span data-stu-id="c8b27-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="c8b27-132">Contém funções para e/s formatada, como `printf` a função.</span><span class="sxs-lookup"><span data-stu-id="c8b27-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="c8b27-133">Atributo AutoOpen</span><span class="sxs-lookup"><span data-stu-id="c8b27-133">AutoOpen Attribute</span></span>

<span data-ttu-id="c8b27-134">Você pode aplicar o `AutoOpen` atributo a um assembly se desejar abrir automaticamente um namespace ou módulo quando o assembly for referenciado.</span><span class="sxs-lookup"><span data-stu-id="c8b27-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="c8b27-135">Você também pode aplicar o `AutoOpen` atributo a um módulo para abrir esse módulo automaticamente quando o namespace ou o módulo pai for aberto.</span><span class="sxs-lookup"><span data-stu-id="c8b27-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="c8b27-136">Para obter mais informações, consulte [classe Core.](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)AutoOpenAttribute.</span><span class="sxs-lookup"><span data-stu-id="c8b27-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="c8b27-137">Atributo RequireQualifiedAccess</span><span class="sxs-lookup"><span data-stu-id="c8b27-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="c8b27-138">Alguns módulos, registros ou tipos de União podem especificar o `RequireQualifiedAccess` atributo.</span><span class="sxs-lookup"><span data-stu-id="c8b27-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="c8b27-139">Ao referenciar elementos desses módulos, registros ou uniões, você deve usar um nome qualificado, independentemente de você incluir uma declaração de importação.</span><span class="sxs-lookup"><span data-stu-id="c8b27-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="c8b27-140">Se você usar esse atributo estrategicamente em tipos que definem nomes comumente usados, você ajudará a evitar colisões de nomes e, portanto, tornará o código mais resiliente às alterações nas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="c8b27-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="c8b27-141">Para obter mais informações, consulte [classe Core. RequireQualifiedAccessAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="c8b27-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8b27-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8b27-142">See also</span></span>

- [<span data-ttu-id="c8b27-143">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="c8b27-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c8b27-144">Namespaces</span><span class="sxs-lookup"><span data-stu-id="c8b27-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="c8b27-145">Módulos</span><span class="sxs-lookup"><span data-stu-id="c8b27-145">Modules</span></span>](modules.md)

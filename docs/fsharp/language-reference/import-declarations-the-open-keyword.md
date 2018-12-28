---
title: 'Declarações de importação: A palavra-chave open'
description: Saiba mais sobre F# importar declarações e como elas especificam um módulo ou namespace cujos elementos que você pode referenciar sem usar um nome totalmente qualificado.
ms.date: 05/16/2016
ms.openlocfilehash: 261ffdfdea2860db72b052b2ffeb5c7e5d652c24
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610314"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="0d0e0-103">Declarações de importação: O `open` palavra-chave</span><span class="sxs-lookup"><span data-stu-id="0d0e0-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="0d0e0-104">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="0d0e0-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="0d0e0-106">Uma *declaração da importação* Especifica um módulo ou namespace cujos elementos que você pode referenciar sem usar um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d0e0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d0e0-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="0d0e0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d0e0-108">Remarks</span></span>

<span data-ttu-id="0d0e0-109">Referência de código usando o caminho totalmente qualificado de namespace ou módulo sempre pode criar código que é difícil de escrever, ler e manter.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="0d0e0-110">Em vez disso, você pode usar o `open` palavra-chave para usados com frequência módulos e namespaces para que quando você faz referência a um membro desse módulo ou namespace, você pode usar a forma abreviada do nome em vez do nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="0d0e0-111">Essa palavra-chave é semelhante para o `using` palavra-chave em c#, `using namespace` no Visual C++, e `Imports` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="0d0e0-112">O módulo ou namespace fornecido deve ser no mesmo projeto ou em um projeto referenciado ou um assembly.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="0d0e0-113">Se não for, você pode adicionar uma referência ao projeto ou usar o `-reference` comando`-`opção de linha (ou sua abreviação `-r`).</span><span class="sxs-lookup"><span data-stu-id="0d0e0-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="0d0e0-114">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="0d0e0-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="0d0e0-115">A declaração de importação disponibiliza os nomes no código que segue a declaração, até o fim do delimitador namespace, módulo ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="0d0e0-116">Quando você usa várias declarações de importação, eles devem aparecer em linhas separadas.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="0d0e0-117">O código a seguir mostra o uso do `open` palavra-chave para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="0d0e0-118">O F# compilador não emite um erro ou aviso quando ambiguidades ocorrem quando o mesmo nome ocorre em mais de um namespace ou módulo aberto.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="0d0e0-119">Quando ambiguidades ocorrem, F# dá preferência para o namespace ou módulo abertos mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="0d0e0-120">Por exemplo, no código a seguir, `empty` significa `Seq.empty`, embora `empty` está localizado em ambos os `List` e `Seq` módulos.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="0d0e0-121">Portanto, tenha cuidado ao abrir módulos ou namespaces, como `List` ou `Seq` que contêm membros que tenham nomes idênticos; em vez disso, considere usar os nomes qualificados.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="0d0e0-122">Você deve evitar qualquer situação na qual o código é dependente na ordem em que as declarações de importação.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="0d0e0-123">Namespaces que estão abertos por padrão</span><span class="sxs-lookup"><span data-stu-id="0d0e0-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="0d0e0-124">Alguns namespaces com tanta frequência são usados em F# que são abertas implicitamente sem a necessidade de uma declaração de importação explícita do código.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="0d0e0-125">A tabela a seguir mostra os namespaces que estão abertos por padrão.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="0d0e0-126">Namespace</span><span class="sxs-lookup"><span data-stu-id="0d0e0-126">Namespace</span></span>|<span data-ttu-id="0d0e0-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d0e0-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="0d0e0-128">Contém o básico F# digite definições para tipos internos, como `int` e `float`.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="0d0e0-129">Contém operações aritméticas básicas, como `+` e `*`.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="0d0e0-130">Contém classes de coleção imutável, como `List` e `Array`.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="0d0e0-131">Contém tipos para construções de controle, como a avaliação lenta e fluxos de trabalho assíncronos.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="0d0e0-132">Contém funções de e/s formatado, tais como o `printf` função.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="0d0e0-133">Atributo AutoOpen</span><span class="sxs-lookup"><span data-stu-id="0d0e0-133">AutoOpen Attribute</span></span>

<span data-ttu-id="0d0e0-134">Você pode aplicar o `AutoOpen` atributo a um assembly, se você quiser abrir automaticamente um namespace ou módulo quando o assembly for referenciado.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="0d0e0-135">Você também pode aplicar o `AutoOpen` de atributo a um módulo para abrir o módulo automaticamente quando o namespace ou módulo pai é aberto.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="0d0e0-136">Para obter mais informações, consulte [classe Core. autoopenattribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="0d0e0-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="0d0e0-137">Atributo RequireQualifiedAccess</span><span class="sxs-lookup"><span data-stu-id="0d0e0-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="0d0e0-138">Alguns módulos, registros ou tipos de união podem especificar o `RequireQualifiedAccess` atributo.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="0d0e0-139">Ao fazer referência a elementos desses módulos, registros ou uniões, você deve usar um nome qualificado, independentemente se você incluir uma declaração de importação.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="0d0e0-140">Se você usar esse atributo estrategicamente em nomes de tipos que definem comumente usados, ajudar a evitar colisões de nome e, portanto, tornar o código mais resiliente às mudanças nas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="0d0e0-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="0d0e0-141">Para obter mais informações, consulte [classe Core. requirequalifiedaccessattribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="0d0e0-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d0e0-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d0e0-142">See also</span></span>

- [<span data-ttu-id="0d0e0-143"># Referência da linguagem</span><span class="sxs-lookup"><span data-stu-id="0d0e0-143"># Language Reference</span></span>](index.md)
- [<span data-ttu-id="0d0e0-144">Namespaces</span><span class="sxs-lookup"><span data-stu-id="0d0e0-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="0d0e0-145">Módulos</span><span class="sxs-lookup"><span data-stu-id="0d0e0-145">Modules</span></span>](modules.md)
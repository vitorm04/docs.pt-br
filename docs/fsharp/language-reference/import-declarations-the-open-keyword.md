---
title: 'Declarações de importação: a palavra-chave open'
description: Saiba mais sobre as declarações de importação F# e como elas especificam um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021535"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="48557-103">Declarações de Importação: a palavra-chave `open`</span><span class="sxs-lookup"><span data-stu-id="48557-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="48557-104">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="48557-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="48557-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="48557-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="48557-106">Uma *declaração de importação* especifica um módulo ou namespace cujos elementos você pode referenciar sem usar um nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="48557-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="48557-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48557-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="48557-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="48557-108">Remarks</span></span>

<span data-ttu-id="48557-109">Fazendo referência ao código usando o namespace ou o caminho do módulo totalmente qualificados, cada vez pode criar um código difícil de escrever, ler e manter.</span><span class="sxs-lookup"><span data-stu-id="48557-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="48557-110">Em vez disso, `open` você pode usar a palavra-chave para módulos e namespaces usados com freqüência para que, quando você referenciar um membro desse módulo ou namespace, você pode usar a forma curta do nome em vez do nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="48557-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="48557-111">Esta palavra-chave é `using` semelhante à palavra-chave em C#, `using namespace` no Visual C++, e `Imports` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="48557-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="48557-112">O módulo ou namespace fornecido deve estar no mesmo projeto ou em um projeto ou montagem referenciado.</span><span class="sxs-lookup"><span data-stu-id="48557-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="48557-113">Se não for, você pode adicionar uma referência `-reference` ao projeto, ou usar a opção `-r`de linha de comando (ou sua abreviação, ).</span><span class="sxs-lookup"><span data-stu-id="48557-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="48557-114">Para obter mais informações, consulte [Opções do compilador](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="48557-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="48557-115">A declaração de importação disponibiliza os nomes no código que segue a declaração, até o final do espaço de nome, módulo ou arquivo de encerramento.</span><span class="sxs-lookup"><span data-stu-id="48557-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="48557-116">Quando você usa várias declarações de importação, elas devem aparecer em linhas separadas.</span><span class="sxs-lookup"><span data-stu-id="48557-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="48557-117">O código a seguir `open` mostra o uso da palavra-chave para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="48557-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="48557-118">O compilador F# não emite um erro ou aviso quando as ambiguidades ocorrem quando o mesmo nome ocorre em mais de um módulo aberto ou namespace.</span><span class="sxs-lookup"><span data-stu-id="48557-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="48557-119">Quando ocorrem ambiguidades, F# dá preferência ao módulo ou namespace mais recentemente aberto.</span><span class="sxs-lookup"><span data-stu-id="48557-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="48557-120">Por exemplo, no código `empty` `Seq.empty`a seguir, significa , `empty` embora `Seq` esteja localizado tanto nos módulos quanto nos `List` módulos.</span><span class="sxs-lookup"><span data-stu-id="48557-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="48557-121">Portanto, tenha cuidado ao abrir módulos ou `List` `Seq` namespaces, tais como ou que contenham membros com nomes idênticos; em vez disso, considere usar os nomes qualificados.</span><span class="sxs-lookup"><span data-stu-id="48557-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="48557-122">Você deve evitar qualquer situação em que o código dependa da ordem das declarações de importação.</span><span class="sxs-lookup"><span data-stu-id="48557-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="48557-123">Namespaces que são abertos por padrão</span><span class="sxs-lookup"><span data-stu-id="48557-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="48557-124">Alguns namespaces são tão freqüentemente usados no código F# que são abertos implicitamente sem a necessidade de uma declaração de importação explícita.</span><span class="sxs-lookup"><span data-stu-id="48557-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="48557-125">A tabela a seguir mostra os namespaces que estão abertos por padrão.</span><span class="sxs-lookup"><span data-stu-id="48557-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="48557-126">Namespace</span><span class="sxs-lookup"><span data-stu-id="48557-126">Namespace</span></span>|<span data-ttu-id="48557-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="48557-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="48557-128">Contém definições básicas do tipo F# `int` para `float`tipos incorporados, tais como e .</span><span class="sxs-lookup"><span data-stu-id="48557-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="48557-129">Contém operações aritméticas básicas como `+` e `*`.</span><span class="sxs-lookup"><span data-stu-id="48557-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="48557-130">Contém classes de coleta imutáveis, tais como `List` e `Array`.</span><span class="sxs-lookup"><span data-stu-id="48557-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="48557-131">Contém tipos de construções de controle, como avaliação preguiçosa e fluxos de trabalho assíncronos.</span><span class="sxs-lookup"><span data-stu-id="48557-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="48557-132">Contém funções para IO formatado, como a `printf` função.</span><span class="sxs-lookup"><span data-stu-id="48557-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="48557-133">Atributo autoaberto</span><span class="sxs-lookup"><span data-stu-id="48557-133">AutoOpen Attribute</span></span>

<span data-ttu-id="48557-134">Você pode `AutoOpen` aplicar o atributo a um conjunto se quiser abrir automaticamente um namespace ou módulo quando o conjunto for referenciado.</span><span class="sxs-lookup"><span data-stu-id="48557-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="48557-135">Você também pode `AutoOpen` aplicar o atributo a um módulo para abrir automaticamente esse módulo quando o módulo pai ou namespace for aberto.</span><span class="sxs-lookup"><span data-stu-id="48557-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="48557-136">Para obter mais informações, consulte [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="48557-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="48557-137">DeexigiraaaaaaadesAtributo de</span><span class="sxs-lookup"><span data-stu-id="48557-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="48557-138">Alguns módulos, registros ou tipos `RequireQualifiedAccess` de união podem especificar o atributo.</span><span class="sxs-lookup"><span data-stu-id="48557-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="48557-139">Quando você faz referência a elementos desses módulos, registros ou sindicatos, você deve usar um nome qualificado, independentemente de incluir uma declaração de importação.</span><span class="sxs-lookup"><span data-stu-id="48557-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="48557-140">Se você usar esse atributo estrategicamente em tipos que definem nomes comumente usados, você ajuda a evitar colisões de nomes e, assim, tornar o código mais resistente às alterações nas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="48557-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="48557-141">Para obter mais informações, consulte [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="48557-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="48557-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="48557-142">See also</span></span>

- [<span data-ttu-id="48557-143">Referência de idioma F#</span><span class="sxs-lookup"><span data-stu-id="48557-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="48557-144">Namespaces</span><span class="sxs-lookup"><span data-stu-id="48557-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="48557-145">Módulos</span><span class="sxs-lookup"><span data-stu-id="48557-145">Modules</span></span>](modules.md)

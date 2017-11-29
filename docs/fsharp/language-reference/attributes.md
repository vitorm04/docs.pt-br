---
title: Atributos (F#)
description: "Saiba como habilitar o F # atributos metadados a ser aplicado a uma construção de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 95c001e6-3708-4d04-a850-d855f78eb51e
ms.openlocfilehash: 88098e51d19a86f501c35abe3408524378f147b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="attributes"></a><span data-ttu-id="7e19f-104">Atributos</span><span class="sxs-lookup"><span data-stu-id="7e19f-104">Attributes</span></span>

<span data-ttu-id="7e19f-105">Atributos habilitam metadados a ser aplicado a uma construção de programação.</span><span class="sxs-lookup"><span data-stu-id="7e19f-105">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e19f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e19f-106">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="7e19f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e19f-107">Remarks</span></span>

<span data-ttu-id="7e19f-108">Na sintaxe anterior, o *destino* é opcional e, se presente, especifica o tipo de entidade de programa que o atributo se aplica ao.</span><span class="sxs-lookup"><span data-stu-id="7e19f-108">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="7e19f-109">Os valores válidos para *destino* são mostrados na tabela mostrada posteriormente neste documento.</span><span class="sxs-lookup"><span data-stu-id="7e19f-109">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="7e19f-110">O *nome do atributo* refere-se ao nome (possivelmente qualificado com namespaces) de um tipo de atributo válido, com ou sem o sufixo `Attribute` que geralmente é usado em nomes de tipo de atributo.</span><span class="sxs-lookup"><span data-stu-id="7e19f-110">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="7e19f-111">Por exemplo, o tipo `ObsoleteAttribute` pode ser reduzido para apenas `Obsolete` neste contexto.</span><span class="sxs-lookup"><span data-stu-id="7e19f-111">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="7e19f-112">O *argumentos* são os argumentos para o construtor para o tipo de atributo.</span><span class="sxs-lookup"><span data-stu-id="7e19f-112">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="7e19f-113">Se um atributo tem um construtor padrão, a lista de argumentos e parênteses podem ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="7e19f-113">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="7e19f-114">Suportam a atributos argumentos posicionais e argumentos nomeados.</span><span class="sxs-lookup"><span data-stu-id="7e19f-114">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="7e19f-115">*Argumentos posicionais* são argumentos que são usados na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="7e19f-115">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="7e19f-116">Argumentos nomeados podem ser usados se o atributo tem propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="7e19f-116">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="7e19f-117">Você pode definir essas configurações usando a sintaxe a seguir na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="7e19f-117">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="7e19f-118">Tais inicializações de propriedade podem estar em qualquer ordem, mas eles devem seguir argumentos posicionais.</span><span class="sxs-lookup"><span data-stu-id="7e19f-118">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="7e19f-119">A seguir está um exemplo de um atributo que usa argumentos posicionais e inicializações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="7e19f-119">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="7e19f-120">Neste exemplo, o atributo é `DllImportAttribute`, aqui é usado em forma abreviada.</span><span class="sxs-lookup"><span data-stu-id="7e19f-120">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="7e19f-121">O primeiro argumento é um parâmetro posicional e o segundo é uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="7e19f-121">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="7e19f-122">Os atributos são uma construção de programação do .NET que permite que um objeto conhecido como um *atributo* a ser associado um tipo ou outro elemento do programa.</span><span class="sxs-lookup"><span data-stu-id="7e19f-122">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="7e19f-123">O elemento do programa para o qual um atributo é aplicado é conhecido como o *atributo de destino*.</span><span class="sxs-lookup"><span data-stu-id="7e19f-123">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="7e19f-124">O atributo normalmente contém metadados sobre seu destino.</span><span class="sxs-lookup"><span data-stu-id="7e19f-124">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="7e19f-125">Nesse contexto, metadados podem ser qualquer dados sobre o tipo diferente de seus campos e membros.</span><span class="sxs-lookup"><span data-stu-id="7e19f-125">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="7e19f-126">Atributos em F # podem ser aplicados para as seguintes construções de programação: funções, métodos, assemblies, módulos, tipos (classes, registros, estruturas, interfaces, delegados, enumerações, uniões e assim por diante), construtores, propriedades, campos, parâmetros, parâmetros de tipo e valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="7e19f-126">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="7e19f-127">Atributos não são permitidos em `let` associações dentro de classes, expressões ou expressões de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7e19f-127">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="7e19f-128">Normalmente, a declaração de atributo aparece diretamente antes da declaração do atributo de destino.</span><span class="sxs-lookup"><span data-stu-id="7e19f-128">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="7e19f-129">Várias declarações de atributo podem ser usadas em conjunto, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="7e19f-129">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="7e19f-130">Você pode consultar os atributos em tempo de execução por meio de reflexão do .NET.</span><span class="sxs-lookup"><span data-stu-id="7e19f-130">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="7e19f-131">Você pode declarar vários atributos individualmente, como no exemplo de código anterior, ou você pode declará-los em um conjunto de colchetes, se você usar um ponto e vírgula para separar os atributos individuais e construtores, conforme mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="7e19f-131">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="7e19f-132">Atributos encontrados normalmente incluem o `Obsolete` atributo, atributos de considerações de segurança, atributos de COM suporte, os atributos relacionados à propriedade de código e atributos que indica se um tipo pode ser serializado.</span><span class="sxs-lookup"><span data-stu-id="7e19f-132">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="7e19f-133">O exemplo a seguir demonstra o uso do `Obsolete` atributo.</span><span class="sxs-lookup"><span data-stu-id="7e19f-133">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="7e19f-134">Para os destinos de atributo `assembly` e `module`, aplicar os atributos para um nível superior `do` de associação no seu assembly.</span><span class="sxs-lookup"><span data-stu-id="7e19f-134">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="7e19f-135">Você pode incluir a palavra `assembly` ou `module` na declaração de atributo, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="7e19f-135">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="7e19f-136">Se você omitir o atributo de destino para um atributo aplicado a um `do` de associação, o compilador F # tentará determinar o atributo de destino que faça sentido para o atributo.</span><span class="sxs-lookup"><span data-stu-id="7e19f-136">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="7e19f-137">Muitas classes de atributo tem um atributo de tipo `System.AttributeUsageAttribute` que inclui informações sobre os destinos possíveis com suporte para esse atributo.</span><span class="sxs-lookup"><span data-stu-id="7e19f-137">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="7e19f-138">Se o `System.AttributeUsageAttribute` indica que o atributo oferece suporte a funções como destinos, o atributo é necessário para aplicar ao ponto de entrada principal do programa.</span><span class="sxs-lookup"><span data-stu-id="7e19f-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="7e19f-139">Se o `System.AttributeUsageAttribute` indica que o atributo oferece suporte a assemblies como destinos, o compilador usa o atributo a ser aplicado ao assembly.</span><span class="sxs-lookup"><span data-stu-id="7e19f-139">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="7e19f-140">A maioria dos atributos não se aplicam às funções e assemblies, mas em casos em que eles fazem, o atributo é feito para aplicar a função principal do programa.</span><span class="sxs-lookup"><span data-stu-id="7e19f-140">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="7e19f-141">Se o atributo de destino for especificado explicitamente, o atributo é aplicado ao destino especificado.</span><span class="sxs-lookup"><span data-stu-id="7e19f-141">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="7e19f-142">Embora normalmente não é necessário especificar o atributo de destino explicitamente, os valores válidos para *destino* em um atributo são mostrados na tabela a seguir, junto com exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="7e19f-142">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="7e19f-143">Atributo de destino</span><span class="sxs-lookup"><span data-stu-id="7e19f-143">Attribute target</span></span></td>
    <th><span data-ttu-id="7e19f-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e19f-144">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="7e19f-145">assembly</span><span class="sxs-lookup"><span data-stu-id="7e19f-145">assembly</span></span></td>
    <td><span data-ttu-id="7e19f-146">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="7e19f-146">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="7e19f-147">return</span><span class="sxs-lookup"><span data-stu-id="7e19f-147">return</span></span></td>
    <td><span data-ttu-id="7e19f-148">' permitem function1 x: [<return: Obsolete>] int = x + 1'</span><span class="sxs-lookup"><span data-stu-id="7e19f-148">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="7e19f-149">campo</span><span class="sxs-lookup"><span data-stu-id="7e19f-149">field</span></span></td>
    <td><span data-ttu-id="7e19f-150">' [<field: DefaultValue>] x: int mutável val'</span><span class="sxs-lookup"><span data-stu-id="7e19f-150">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="7e19f-151">propriedade</span><span class="sxs-lookup"><span data-stu-id="7e19f-151">property</span></span></td>
    <td><span data-ttu-id="7e19f-152">' [<property: Obsolete>] isso. MyProperty = x'</span><span class="sxs-lookup"><span data-stu-id="7e19f-152">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="7e19f-153">Param</span><span class="sxs-lookup"><span data-stu-id="7e19f-153">param</span></span></td>
    <td><span data-ttu-id="7e19f-154">' membro isso. Meumetodo ([<param: Out>] x: ref<int>) = x: = 10'</span><span class="sxs-lookup"><span data-stu-id="7e19f-154">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="7e19f-155">tipo</span><span class="sxs-lookup"><span data-stu-id="7e19f-155">type</span></span></td>
    <td><span data-ttu-id="7e19f-156">
        ```
        [<type: StructLayout(Sequential)>] Digite MyStruct = struct x: bytes y: int final```
    </span><span class="sxs-lookup"><span data-stu-id="7e19f-156">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="7e19f-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e19f-157">See Also</span></span>

[<span data-ttu-id="7e19f-158">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="7e19f-158">F# Language Reference</span></span>](index.md)

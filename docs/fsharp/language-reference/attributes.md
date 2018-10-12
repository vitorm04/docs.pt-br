---
title: Atributos (F#)
description: 'Saiba como F # atributos permitem que os metadados a ser aplicado a um constructo de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: 3e7f1d0ff383e1070b3db72e633f80ea37150548
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121743"
---
# <a name="attributes"></a><span data-ttu-id="5d3bb-103">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d3bb-103">Attributes</span></span>

<span data-ttu-id="5d3bb-104">Atributos permitem os metadados a ser aplicado a um constructo de programação.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d3bb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d3bb-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="5d3bb-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d3bb-106">Remarks</span></span>

<span data-ttu-id="5d3bb-107">Na sintaxe anterior, o *destino* é opcional e, se presente, especifica o tipo de entidade de programa que o atributo se aplica a.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="5d3bb-108">Os valores válidos para *destino* são mostrados na tabela que aparece mais adiante neste documento.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="5d3bb-109">O *nome do atributo* refere-se ao nome (possivelmente qualificado com namespaces) de um tipo de atributo válido, com ou sem o sufixo `Attribute` que geralmente é usado em nomes de tipo de atributo.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="5d3bb-110">Por exemplo, o tipo `ObsoleteAttribute` pode ser reduzido para apenas `Obsolete` neste contexto.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="5d3bb-111">O *argumentos* são os argumentos para o construtor para o tipo de atributo.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="5d3bb-112">Se um atributo tem um construtor padrão, a lista de argumentos e os parênteses podem ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="5d3bb-113">Suportam a atributos argumentos posicionais e argumentos nomeados.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="5d3bb-114">*Argumentos posicionais* são argumentos que são usados na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="5d3bb-115">Argumentos nomeados podem ser usados se o atributo tem propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="5d3bb-116">Você pode definir esses itens usando a sintaxe a seguir na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-116">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="5d3bb-117">Essas inicializações de propriedade podem estar em qualquer ordem, mas eles devem seguir argumentos posicionais.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="5d3bb-118">A seguir está um exemplo de um atributo que usa argumentos posicionais e inicializações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="5d3bb-119">Neste exemplo, o atributo é `DllImportAttribute`, aqui é usado de forma abreviada.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="5d3bb-120">O primeiro argumento é um parâmetro posicional e o segundo é uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="5d3bb-121">Os atributos são um constructo de programação do .NET que permite que um objeto conhecido como um *atributo* a ser associado um tipo ou outro elemento de programa.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="5d3bb-122">O elemento de programa ao qual um atributo é aplicado é conhecido como o *atributo de destino*.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="5d3bb-123">O atributo geralmente contém metadados sobre seu destino.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="5d3bb-124">Nesse contexto, metadados pode ser quaisquer dados sobre o tipo diferente de seus campos e membros.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="5d3bb-125">Atributos em F # podem ser aplicados para as seguintes construções de programação: funções, métodos, assemblies, módulos, tipos (classes, registros, estruturas, interfaces, delegados, enumerações, uniões e assim por diante), construtores, propriedades, campos, parâmetros, parâmetros de tipo e valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="5d3bb-126">Atributos não são permitidos em `let` associações dentro de classes, expressões ou expressões de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="5d3bb-127">Normalmente, a declaração de atributo aparece diretamente antes da declaração de atributo de destino.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="5d3bb-128">Várias declarações de atributo podem ser usadas em conjunto, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="5d3bb-129">Você pode consultar os atributos em tempo de execução por meio de reflexão do .NET.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="5d3bb-130">Você pode declarar vários atributos individualmente, como no exemplo de código anterior, ou você pode declará-las em um par de colchetes, se você usar um ponto e vírgula para separar os atributos individuais e construtores, conforme mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="5d3bb-131">Atributos encontrados normalmente incluem o `Obsolete` atributos de atributo, atributos para considerações de segurança, para suporte de COM, os atributos relacionados à propriedade do código e atributos que indica se um tipo pode ser serializado.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="5d3bb-132">O exemplo a seguir demonstra o uso do `Obsolete` atributo.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="5d3bb-133">Para os destinos de atributo `assembly` e `module`, você aplica os atributos a um nível superior `do` associação em seu assembly.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="5d3bb-134">Você pode incluir a palavra `assembly` ou `module` na declaração de atributo, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="5d3bb-135">Se você omitir o atributo de destino para um atributo aplicado a um `do` de associação, o compilador F # tenta determinar o atributo de destino que faça sentido para o atributo.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="5d3bb-136">Muitas classes de atributo tem um atributo de tipo `System.AttributeUsageAttribute` que inclui informações sobre os destinos possíveis com suporte para esse atributo.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="5d3bb-137">Se o `System.AttributeUsageAttribute` indica que o atributo dá suporte a funções como destinos, o atributo é obtido para aplicar ao ponto de entrada principal do programa.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="5d3bb-138">Se o `System.AttributeUsageAttribute` indica que o atributo dá suporte a assemblies como destinos, o compilador usa o atributo a ser aplicado ao assembly.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="5d3bb-139">A maioria dos atributos não se aplicam a funções e assemblies, mas em casos em que eles fazem, o atributo é necessário para aplicar a função de principal do programa.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="5d3bb-140">Se o atributo de destino for especificado explicitamente, o atributo é aplicado no destino especificado.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="5d3bb-141">Embora normalmente não é necessário especificar o atributo de destino explicitamente, os valores válidos para *destino* em um atributo são mostrados na tabela a seguir, junto com exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="5d3bb-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="5d3bb-142">Atributo de destino</span><span class="sxs-lookup"><span data-stu-id="5d3bb-142">Attribute target</span></span></td>
    <th><span data-ttu-id="5d3bb-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d3bb-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="5d3bb-144">assembly</span><span class="sxs-lookup"><span data-stu-id="5d3bb-144">assembly</span></span></td>
    <td><span data-ttu-id="5d3bb-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="5d3bb-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="5d3bb-146">return</span><span class="sxs-lookup"><span data-stu-id="5d3bb-146">return</span></span></td>
    <td><span data-ttu-id="5d3bb-147">' Permitir que função1 x: [<return: Obsolete>] int = x + 1'</span><span class="sxs-lookup"><span data-stu-id="5d3bb-147">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="5d3bb-148">campo</span><span class="sxs-lookup"><span data-stu-id="5d3bb-148">field</span></span></td>
    <td><span data-ttu-id="5d3bb-149">' [<field: DefaultValue>] val de x: int mutável '</span><span class="sxs-lookup"><span data-stu-id="5d3bb-149">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="5d3bb-150">propriedade</span><span class="sxs-lookup"><span data-stu-id="5d3bb-150">property</span></span></td>
    <td><span data-ttu-id="5d3bb-151">' [<property: Obsolete>] isso. MyProperty = x'</span><span class="sxs-lookup"><span data-stu-id="5d3bb-151">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="5d3bb-152">param</span><span class="sxs-lookup"><span data-stu-id="5d3bb-152">param</span></span></td>
    <td><span data-ttu-id="5d3bb-153">' membro isso. MyMethod ([<param: Out>] x: ref<int>) = x: = 10'</span><span class="sxs-lookup"><span data-stu-id="5d3bb-153">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="5d3bb-154">tipo</span><span class="sxs-lookup"><span data-stu-id="5d3bb-154">type</span></span></td>
    <td><span data-ttu-id="5d3bb-155">
        ```
        [<type: StructLayout(Sequential)>] Digite MyStruct = struct x: y byte: final do int ```
    </span><span class="sxs-lookup"><span data-stu-id="5d3bb-155">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="5d3bb-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d3bb-156">See also</span></span>

- [<span data-ttu-id="5d3bb-157">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="5d3bb-157">F# Language Reference</span></span>](index.md)

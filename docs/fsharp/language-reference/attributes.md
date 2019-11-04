---
title: Atributos
description: Saiba como F# os atributos permitem que os metadados sejam aplicados a um constructo de programação.
ms.date: 05/16/2016
ms.openlocfilehash: 223263f5789b0fc7eb2b3ef2905f6436980bd14a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424793"
---
# <a name="attributes"></a><span data-ttu-id="68362-103">Atributos</span><span class="sxs-lookup"><span data-stu-id="68362-103">Attributes</span></span>

<span data-ttu-id="68362-104">Os atributos permitem que os metadados sejam aplicados a um constructo de programação.</span><span class="sxs-lookup"><span data-stu-id="68362-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="68362-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68362-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="68362-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="68362-106">Remarks</span></span>

<span data-ttu-id="68362-107">Na sintaxe anterior, o *destino* é opcional e, se presente, especifica o tipo de entidade de programa à qual o atributo se aplica.</span><span class="sxs-lookup"><span data-stu-id="68362-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="68362-108">Os valores válidos para *destino* são mostrados na tabela que aparece mais adiante neste documento.</span><span class="sxs-lookup"><span data-stu-id="68362-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="68362-109">O *atributo-nome* refere-se ao nome (possivelmente qualificado com namespaces) de um tipo de atributo válido, com ou sem o sufixo `Attribute` que geralmente é usado em nomes de tipo de atributo.</span><span class="sxs-lookup"><span data-stu-id="68362-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="68362-110">Por exemplo, o tipo `ObsoleteAttribute` pode ser reduzido para apenas `Obsolete` neste contexto.</span><span class="sxs-lookup"><span data-stu-id="68362-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="68362-111">Os *argumentos* são os argumentos para o construtor para o tipo de atributo.</span><span class="sxs-lookup"><span data-stu-id="68362-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="68362-112">Se um atributo tiver um construtor sem parâmetros, a lista de argumentos e os parênteses poderão ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="68362-112">If an attribute has a parameterless constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="68362-113">Os atributos dão suporte a argumentos posicionais e argumentos nomeados.</span><span class="sxs-lookup"><span data-stu-id="68362-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="68362-114">*Argumentos posicionais* são argumentos que são usados na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="68362-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="68362-115">Argumentos nomeados podem ser usados se o atributo tiver propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="68362-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="68362-116">Você pode defini-los usando a sintaxe a seguir na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="68362-116">You can set these by using the following syntax in the argument list.</span></span>

```fsharp
property-name = property-value
```

<span data-ttu-id="68362-117">Essas inicializações de propriedade podem estar em qualquer ordem, mas devem seguir quaisquer argumentos posicionais.</span><span class="sxs-lookup"><span data-stu-id="68362-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="68362-118">Veja a seguir um exemplo de um atributo que usa argumentos posicionais e inicializações de propriedade:</span><span class="sxs-lookup"><span data-stu-id="68362-118">The following is an example of an attribute that uses positional arguments and property initializations:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="68362-119">Neste exemplo, o atributo é `DllImportAttribute`, aqui usado na forma abreviada.</span><span class="sxs-lookup"><span data-stu-id="68362-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="68362-120">O primeiro argumento é um parâmetro posicional e o segundo é uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="68362-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="68362-121">Os atributos são uma construção de programação .NET que permite que um objeto conhecido como *atributo* seja associado a um tipo ou outro elemento de programa.</span><span class="sxs-lookup"><span data-stu-id="68362-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="68362-122">O elemento Program ao qual um atributo é aplicado é conhecido como o *destino do atributo*.</span><span class="sxs-lookup"><span data-stu-id="68362-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="68362-123">O atributo geralmente contém metadados sobre seu destino.</span><span class="sxs-lookup"><span data-stu-id="68362-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="68362-124">Nesse contexto, os metadados podem ser qualquer dado sobre o tipo que não seja seus campos e membros.</span><span class="sxs-lookup"><span data-stu-id="68362-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="68362-125">Os atributos F# in podem ser aplicados às seguintes construções de programação: funções, métodos, assemblies, módulos, tipos (classes, registros, estruturas, interfaces, delegados, enumerações, uniões e assim por diante), construtores, propriedades, campos, parâmetros, parâmetros de tipo e valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="68362-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="68362-126">Atributos não são permitidos em associações `let` dentro de classes, expressões ou expressões de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="68362-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="68362-127">Normalmente, a declaração de atributo aparece diretamente antes da declaração do destino do atributo.</span><span class="sxs-lookup"><span data-stu-id="68362-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="68362-128">Várias declarações de atributo podem ser usadas juntas, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="68362-128">Multiple attribute declarations can be used together, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="68362-129">Você pode consultar atributos em tempo de execução usando a reflexão do .NET.</span><span class="sxs-lookup"><span data-stu-id="68362-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="68362-130">Você pode declarar vários atributos individualmente, como no exemplo de código anterior, ou pode declará-los em um conjunto de colchetes se usar um ponto e vírgula para separar os atributos e construtores individuais, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="68362-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="68362-131">Normalmente, os atributos encontrados incluem o atributo `Obsolete`, atributos para considerações de segurança, atributos para suporte COM, atributos relacionados à propriedade de código e atributos que indicam se um tipo pode ser serializado.</span><span class="sxs-lookup"><span data-stu-id="68362-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="68362-132">O exemplo a seguir demonstra o uso do atributo `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="68362-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="68362-133">Para os destinos de atributo `assembly` e `module`, você aplica os atributos a uma associação de `do` de nível superior em seu assembly.</span><span class="sxs-lookup"><span data-stu-id="68362-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="68362-134">Você pode incluir a palavra `assembly` ou `module` na declaração de atributo, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="68362-134">You can include the word `assembly` or `module` in the attribute declaration, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="68362-135">Se você omitir o destino de atributo para um atributo aplicado a uma associação de F# `do`, o compilador tentará determinar o destino do atributo que faz sentido para esse atributo.</span><span class="sxs-lookup"><span data-stu-id="68362-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="68362-136">Muitas classes de atributo têm um atributo do tipo `System.AttributeUsageAttribute` que inclui informações sobre os possíveis destinos com suporte para esse atributo.</span><span class="sxs-lookup"><span data-stu-id="68362-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="68362-137">Se o `System.AttributeUsageAttribute` indicar que o atributo oferece suporte a funções como destinos, o atributo será levado para ser aplicado ao ponto de entrada principal do programa.</span><span class="sxs-lookup"><span data-stu-id="68362-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="68362-138">Se o `System.AttributeUsageAttribute` indicar que o atributo dá suporte a assemblies como destinos, o compilador usará o atributo para aplicar ao assembly.</span><span class="sxs-lookup"><span data-stu-id="68362-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="68362-139">A maioria dos atributos não se aplica a funções e assemblies, mas nos casos em que eles fazem, o atributo é levado para ser aplicado à função main do programa.</span><span class="sxs-lookup"><span data-stu-id="68362-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="68362-140">Se o atributo target for especificado explicitamente, o atributo será aplicado ao destino especificado.</span><span class="sxs-lookup"><span data-stu-id="68362-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="68362-141">Embora você normalmente não precise especificar o destino do atributo explicitamente, os valores válidos para o *destino* em um atributo juntamente com exemplos de uso são mostrados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="68362-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute along with examples of usage are shown in the following table:</span></span>

<table>
  <tr>
    <th><span data-ttu-id="68362-142">Destino do atributo</span><span class="sxs-lookup"><span data-stu-id="68362-142">Attribute target</span></span></td>
    <th><span data-ttu-id="68362-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68362-143">Example</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="68362-144">assembly</span><span class="sxs-lookup"><span data-stu-id="68362-144">assembly</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="68362-145">return</span><span class="sxs-lookup"><span data-stu-id="68362-145">return</span></span></td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="68362-146">campo</span><span class="sxs-lookup"><span data-stu-id="68362-146">field</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="68362-147">propriedade</span><span class="sxs-lookup"><span data-stu-id="68362-147">property</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="68362-148">param</span><span class="sxs-lookup"><span data-stu-id="68362-148">param</span></span></td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="68362-149">tipo</span><span class="sxs-lookup"><span data-stu-id="68362-149">type</span></span></td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(Sequential)&gt;]
type MyStruct =
struct
x : byte
y : int
end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="68362-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68362-150">See also</span></span>

- [<span data-ttu-id="68362-151">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="68362-151">F# Language Reference</span></span>](index.md)

---
title: Diretiva x:Arguments
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071587"
---
# <a name="xarguments-directive"></a><span data-ttu-id="12e08-102">Diretiva x:Arguments</span><span class="sxs-lookup"><span data-stu-id="12e08-102">x:Arguments Directive</span></span>

<span data-ttu-id="12e08-103">Embala argumentos de construção para uma declaração de elemento de objeto construtor não parâmetro no XAML ou para uma declaração de objeto de método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="12e08-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>

## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="12e08-104">Uso do elemento XAML (construtor sem parâmetro)</span><span class="sxs-lookup"><span data-stu-id="12e08-104">XAML Element Usage (Nonparameterless constructor)</span></span>

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="12e08-105">Uso do elemento XAML (método de fábrica)</span><span class="sxs-lookup"><span data-stu-id="12e08-105">XAML Element Usage (factory method)</span></span>

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="12e08-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="12e08-106">XAML Values</span></span>

|||
|-|-|
|`oneOrMoreObjectElements`|<span data-ttu-id="12e08-107">Um ou mais elementos de objeto que especificam argumentos a serem passados para o construtor ou método de fábrica não-parâmetro sem parâmetros de apoio.</span><span class="sxs-lookup"><span data-stu-id="12e08-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="12e08-108">O uso típico é usar o texto de inicialização dentro dos elementos do objeto para especificar os valores reais do argumento.</span><span class="sxs-lookup"><span data-stu-id="12e08-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="12e08-109">Veja a seção Exemplos.</span><span class="sxs-lookup"><span data-stu-id="12e08-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="12e08-110">A ordem dos elementos é significativa.</span><span class="sxs-lookup"><span data-stu-id="12e08-110">The order of the elements is significant.</span></span> <span data-ttu-id="12e08-111">Os tipos XAML em ordem devem corresponder aos tipos e ordem de tipo da sobrecarga do construtor de apoio ou do método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="12e08-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|
|`methodName`|<span data-ttu-id="12e08-112">O nome do método de `x:Arguments` fábrica que deve processar quaisquer argumentos.</span><span class="sxs-lookup"><span data-stu-id="12e08-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="12e08-113">Dependências</span><span class="sxs-lookup"><span data-stu-id="12e08-113">Dependencies</span></span>

<span data-ttu-id="12e08-114">`x:FactoryMethod`pode modificar o escopo `x:Arguments` e o comportamento quando se aplica.</span><span class="sxs-lookup"><span data-stu-id="12e08-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>

<span data-ttu-id="12e08-115">Se `x:FactoryMethod` não for `x:Arguments` especificado, aplica-se a assinaturas alternativas (não padrão) dos construtores de apoio.</span><span class="sxs-lookup"><span data-stu-id="12e08-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>

<span data-ttu-id="12e08-116">Se `x:FactoryMethod` for especificado, `x:Arguments` aplica-se a uma sobrecarga do método nomeado.</span><span class="sxs-lookup"><span data-stu-id="12e08-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>

## <a name="remarks"></a><span data-ttu-id="12e08-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="12e08-117">Remarks</span></span>

<span data-ttu-id="12e08-118">XAML 2006 pode suportar inicialização não padrão através de texto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="12e08-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="12e08-119">No entanto, a aplicação prática de uma técnica de construção de texto de inicialização é limitada.</span><span class="sxs-lookup"><span data-stu-id="12e08-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="12e08-120">O texto de inicialização é tratado como uma única seqüência de texto; portanto, ele só adiciona capacidade para uma inicialização de parâmetro único, a menos que um conversor de tipo seja definido para o comportamento de construção que pode analisar itens de informações personalizadas e delimitadores personalizados da string.</span><span class="sxs-lookup"><span data-stu-id="12e08-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="12e08-121">Além disso, a seqüência de texto para a lógica do objeto é potencialmente um determinado conversor padrão padrão do analisador XAML para manusear primitivos que não seja uma seqüência de string verdadeira.</span><span class="sxs-lookup"><span data-stu-id="12e08-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>

<span data-ttu-id="12e08-122">O `x:Arguments` uso do XAML não é o uso do elemento de propriedade no sentido típico, porque a marcação diretiva não faz referência ao tipo do elemento do objeto que contém.</span><span class="sxs-lookup"><span data-stu-id="12e08-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="12e08-123">É mais parecido com outras `x:Code` diretivas, como quando o elemento demarca um intervalo no qual a marcação deve ser interpretada como diferente do padrão para o conteúdo infantil.</span><span class="sxs-lookup"><span data-stu-id="12e08-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="12e08-124">Neste caso, o tipo XAML de cada elemento objeto comunica informações sobre os tipos de argumento, que são usados por analisadores XAML para determinar qual método específico de fábrica de construção um `x:Arguments` uso está tentando referenciar.</span><span class="sxs-lookup"><span data-stu-id="12e08-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>

<span data-ttu-id="12e08-125">`x:Arguments`para que um elemento objeto que está sendo construído deve preceder quaisquer outros elementos de propriedade, conteúdo, texto interno ou seqüências de inicialização do elemento objeto.</span><span class="sxs-lookup"><span data-stu-id="12e08-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="12e08-126">Os elementos `x:Arguments` do objeto dentro podem incluir atributos e seqüências de inicialização, conforme permitido por esse tipo XAML e seu método de construção ou fábrica de apoio.</span><span class="sxs-lookup"><span data-stu-id="12e08-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="12e08-127">Para o objeto ou os argumentos, você pode especificar tipos XAML personalizados ou tipos XAML que estão fora do namespace XAML padrão, fazendo referência a mapeamentos de prefixos estabelecidos.</span><span class="sxs-lookup"><span data-stu-id="12e08-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>

<span data-ttu-id="12e08-128">Os processadores XAML usam as seguintes diretrizes `x:Arguments` para determinar como os argumentos especificados devem ser usados para construir um objeto.</span><span class="sxs-lookup"><span data-stu-id="12e08-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="12e08-129">Se `x:FactoryMethod` for especificado, as informações `x:FactoryMethod` serão comparadas `x:FactoryMethod` com as especificadas (observe que o valor é o nome do método, e o método nomeado pode ter sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="12e08-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="12e08-130">Se `x:FactoryMethod` não for especificado, as informações são comparadas com o conjunto de todas as sobrecargas de construtores públicos do objeto.</span><span class="sxs-lookup"><span data-stu-id="12e08-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="12e08-131">A lógica de processamento XAML então compara o número de parâmetros e seleciona a sobrecarga com a aridade correspondente.</span><span class="sxs-lookup"><span data-stu-id="12e08-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="12e08-132">Se houver mais de uma correspondência, o processador XAML deve comparar os tipos de parâmetros baseados nos tipos XAML dos elementos do objeto fornecidos.</span><span class="sxs-lookup"><span data-stu-id="12e08-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="12e08-133">Se ainda houver mais de uma correspondência, o comportamento do processador XAML é indefinido.</span><span class="sxs-lookup"><span data-stu-id="12e08-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="12e08-134">Se `x:FactoryMethod` um for especificado, mas o método não puder ser resolvido, um processador XAML deve abrir uma exceção.</span><span class="sxs-lookup"><span data-stu-id="12e08-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>

<span data-ttu-id="12e08-135">Um uso `<x:Arguments>string</x:Arguments>` de atributo XAML é tecnicamente possível.</span><span class="sxs-lookup"><span data-stu-id="12e08-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="12e08-136">No entanto, isso não fornece recursos além do que poderia ser feito de outra forma através de texto de inicialização e conversores de tipo, e usar essa sintaxe não é a intenção de design dos recursos do método de fábrica XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="12e08-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>

## <a name="examples"></a><span data-ttu-id="12e08-137">Exemplos</span><span class="sxs-lookup"><span data-stu-id="12e08-137">Examples</span></span>

<span data-ttu-id="12e08-138">O exemplo a seguir mostra uma assinatura de construtor não-parâmetro, em seguida, o uso XAML dessa `x:Arguments` assinatura.</span><span class="sxs-lookup"><span data-stu-id="12e08-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

```csharp
public class Food {
  private string _name;
  private Int32 _calories;
  public Food(string name, Int32 calories) {
      _name=name;
      _calories=calories;
  }
}
```

```xaml
<my:Food>
  <x:Arguments>
      <x:String>Apple</x:String>
      <x:Int32>150</x:Int32>
  </x:Arguments>
</my:Food>
```

<span data-ttu-id="12e08-139">O exemplo a seguir mostra uma assinatura de método `x:Arguments` de fábrica de destino, em seguida, o uso XAML de que acessa essa assinatura.</span><span class="sxs-lookup"><span data-stu-id="12e08-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

```csharp
public Food TryLookupFood(string name)
{
switch (name) {
  case "Apple": return new Food("Apple",150);
  case "Chocolate": return new Food("Chocolate",200);
  case "Cheese": return new Food("Cheese", 450);
  default: {return new Food(name,0);
}
}
```

```xaml
<my:Food x:FactoryMethod="TryLookupFood">
  <x:Arguments>
      <x:String>Apple</x:String>
  </x:Arguments>
</my:Food>
```

## <a name="see-also"></a><span data-ttu-id="12e08-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="12e08-140">See also</span></span>

- [<span data-ttu-id="12e08-141">Definir tipos personalizados para uso com os serviços XAML do .NET</span><span class="sxs-lookup"><span data-stu-id="12e08-141">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
- [<span data-ttu-id="12e08-142">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="12e08-142">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)

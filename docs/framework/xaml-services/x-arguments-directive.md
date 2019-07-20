---
title: Diretiva x:Arguments
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5bcd629e306169c1f7a61a316d76203827a2d0fe
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364273"
---
# <a name="xarguments-directive"></a><span data-ttu-id="8e1bc-102">Diretiva x:Arguments</span><span class="sxs-lookup"><span data-stu-id="8e1bc-102">x:Arguments Directive</span></span>
<span data-ttu-id="8e1bc-103">Argumentos de construção de pacotes para uma declaração de elemento de objeto de construtor sem parâmetros em XAML ou para uma declaração de objeto de método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="8e1bc-104">Uso do elemento XAML (Construtor sem parâmetros)</span><span class="sxs-lookup"><span data-stu-id="8e1bc-104">XAML Element Usage (Nonparameterless constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="8e1bc-105">Uso do elemento XAML (método de fábrica)</span><span class="sxs-lookup"><span data-stu-id="8e1bc-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8e1bc-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="8e1bc-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="8e1bc-107">Um ou mais elementos de objeto que especificam argumentos a serem passados para o construtor não sem parâmetros ou para o método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="8e1bc-108">O uso típico é usar o texto de inicialização dentro dos elementos de objeto para especificar os valores de argumento reais.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="8e1bc-109">Consulte a seção de exemplos.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="8e1bc-110">A ordem dos elementos é significativa.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-110">The order of the elements is significant.</span></span> <span data-ttu-id="8e1bc-111">Os tipos XAML na ordem devem corresponder aos tipos e à ordem de tipo do construtor de suporte ou sobrecarga de método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="8e1bc-112">O nome do método de fábrica que deve processar `x:Arguments` argumentos.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="8e1bc-113">Dependências</span><span class="sxs-lookup"><span data-stu-id="8e1bc-113">Dependencies</span></span>  
 <span data-ttu-id="8e1bc-114">`x:FactoryMethod`pode modificar o escopo e o comportamento `x:Arguments` em que aplica-se.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="8e1bc-115">Se não `x:FactoryMethod` for especificado, `x:Arguments` aplica-se a assinaturas alternativas (não padrão) dos construtores de backup.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="8e1bc-116">Se `x:FactoryMethod` for especificado, `x:Arguments` aplica-se a uma sobrecarga do método nomeado.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e1bc-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e1bc-117">Remarks</span></span>  
 <span data-ttu-id="8e1bc-118">O XAML 2006 pode dar suporte à inicialização não padrão por meio de texto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="8e1bc-119">No entanto, o aplicativo prático de uma técnica de construção de texto de inicialização é limitado.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="8e1bc-120">O texto de inicialização é tratado como uma única cadeia de texto; Portanto, ele só adiciona recursos para uma única inicialização de parâmetro, a menos que um conversor de tipo seja definido para o comportamento de construção que possa analisar itens de informações personalizados e delimitadores personalizados da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="8e1bc-121">Além disso, a cadeia de caracteres de texto para lógica de objeto é potencialmente um conversor de tipo padrão nativo do analisador XAML para manipular primitivos diferentes de uma cadeia de caracteres verdadeira.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="8e1bc-122">O `x:Arguments` uso do XAML não é o uso do elemento de propriedade no sentido típico, porque a marcação da diretiva não faz referência ao tipo do elemento de objeto recipiente.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="8e1bc-123">Ele é mais semelhante a outras diretivas, como `x:Code` onde o elemento marca um intervalo no qual a marcação deve ser interpretada como diferente do padrão para conteúdo filho.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="8e1bc-124">Nesse caso, o tipo XAML de cada elemento Object comunica informações sobre os tipos de argumentos, que é usado por analisadores XAML para determinar qual assinatura de método de fábrica de construtor `x:Arguments` específica um uso está tentando referenciar.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="8e1bc-125">`x:Arguments`para um elemento de objeto que está sendo construído deve preceder quaisquer outros elementos de propriedade, conteúdo, texto interno ou cadeias de inicialização do elemento Object.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="8e1bc-126">Os elementos de objeto `x:Arguments` dentro podem incluir atributos e cadeias de inicialização, conforme permitido pelo tipo XAML e seu construtor de suporte ou método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="8e1bc-127">Para o objeto ou os argumentos, você pode especificar tipos XAML personalizados ou tipos XAML que, de outra forma, estão fora do namespace XAML padrão referenciando mapeamentos de prefixo estabelecidos.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="8e1bc-128">Os processadores XAML usam as diretrizes a seguir para determinar como os argumentos `x:Arguments` especificados em devem ser usados para construir um objeto.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="8e1bc-129">Se `x:FactoryMethod` for especificado, as informações serão comparadas `x:FactoryMethod` com o especificado (Observe que `x:FactoryMethod` o valor de é o nome do método e o método nomeado pode ter sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="8e1bc-130">Se `x:FactoryMethod` não for especificado, as informações serão comparadas ao conjunto de todas as sobrecargas de construtor público do objeto.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="8e1bc-131">Em seguida, a lógica de processamento XAML compara o número de parâmetros e seleciona a sobrecarga com arity correspondente.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="8e1bc-132">Se houver mais de uma correspondência, o processador XAML deve comparar os tipos dos parâmetros com base nos tipos XAML dos elementos de objeto fornecidos.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="8e1bc-133">Se ainda houver mais de uma correspondência, o comportamento do processador XAML será indefinido.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="8e1bc-134">Se um `x:FactoryMethod` for especificado, mas o método não puder ser resolvido, um processador XAML deverá lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="8e1bc-135">Um uso `<x:Arguments>string</x:Arguments>` de atributo XAML é tecnicamente possível.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="8e1bc-136">No entanto, isso não fornece recursos além do que poderia ser feito de outra forma por meio de texto de inicialização e conversores de tipo, e usar essa sintaxe não é a intenção de design dos recursos de método de fábrica do XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8e1bc-137">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8e1bc-137">Examples</span></span>  
 <span data-ttu-id="8e1bc-138">O exemplo a seguir mostra uma assinatura de construtor sem parâmetros e, em seguida, o `x:Arguments` uso do XAML que acessa essa assinatura.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="8e1bc-139">O exemplo a seguir mostra uma assinatura de método de fábrica de destino e, `x:Arguments` em seguida, o uso do XAML que acessa essa assinatura.</span><span class="sxs-lookup"><span data-stu-id="8e1bc-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e1bc-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e1bc-140">See also</span></span>

- [<span data-ttu-id="8e1bc-141">Definindo tipos personalizados para uso com serviços XAML do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8e1bc-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="8e1bc-142">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="8e1bc-142">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)

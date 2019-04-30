---
title: Diretiva x:Arguments
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a87542513ffeeec7efc526d4218f921d1b7579a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953953"
---
# <a name="xarguments-directive"></a><span data-ttu-id="0057d-102">Diretiva x:Arguments</span><span class="sxs-lookup"><span data-stu-id="0057d-102">x:Arguments Directive</span></span>
<span data-ttu-id="0057d-103">Argumentos de construção de pacotes para uma declaração de elemento de objeto de construtor não padrão no XAML ou para uma declaração de objeto do método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="0057d-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="0057d-104">Uso do elemento XAML (construtor não padrão)</span><span class="sxs-lookup"><span data-stu-id="0057d-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="0057d-105">Uso do elemento XAML (método de fábrica)</span><span class="sxs-lookup"><span data-stu-id="0057d-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="0057d-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="0057d-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="0057d-107">Um ou mais elementos de objeto que especifica argumentos a serem passados para o método de construtor ou fábrica de não-padrão do suporte.</span><span class="sxs-lookup"><span data-stu-id="0057d-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="0057d-108">Uso típico é usar o texto de inicialização dentro de elementos de objeto para especificar os valores de argumento real.</span><span class="sxs-lookup"><span data-stu-id="0057d-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="0057d-109">Consulte a seção de exemplos.</span><span class="sxs-lookup"><span data-stu-id="0057d-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="0057d-110">A ordem dos elementos é significativa.</span><span class="sxs-lookup"><span data-stu-id="0057d-110">The order of the elements is significant.</span></span> <span data-ttu-id="0057d-111">Os tipos XAML na ordem devem correspondem aos tipos e digite a ordem da sobrecarga de método de construtor ou fábrica fazendo backup.</span><span class="sxs-lookup"><span data-stu-id="0057d-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="0057d-112">O nome do método de fábrica que deve processar qualquer `x:Arguments` argumentos.</span><span class="sxs-lookup"><span data-stu-id="0057d-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="0057d-113">Dependências</span><span class="sxs-lookup"><span data-stu-id="0057d-113">Dependencies</span></span>  
 <span data-ttu-id="0057d-114">`x:FactoryMethod` pode modificar o escopo e o comportamento em que `x:Arguments` se aplica.</span><span class="sxs-lookup"><span data-stu-id="0057d-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="0057d-115">Se nenhum `x:FactoryMethod` for especificado, `x:Arguments` se aplica a assinaturas de alternativas (não-padrão) dos construtores de backup.</span><span class="sxs-lookup"><span data-stu-id="0057d-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="0057d-116">Se `x:FactoryMethod` for especificado, `x:Arguments` aplica-se a uma sobrecarga do método nomeado.</span><span class="sxs-lookup"><span data-stu-id="0057d-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0057d-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="0057d-117">Remarks</span></span>  
 <span data-ttu-id="0057d-118">XAML 2006 pode dar suporte a inicialização por meio do texto de inicialização não padrão.</span><span class="sxs-lookup"><span data-stu-id="0057d-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="0057d-119">No entanto, a aplicação prática de uma técnica de construção de texto de inicialização é limitada.</span><span class="sxs-lookup"><span data-stu-id="0057d-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="0057d-120">Texto de inicialização é tratado como uma cadeia de caracteres de texto simples; Portanto, ele apenas adiciona funcionalidade para a inicialização de um único parâmetro, a menos que um conversor de tipo é definido para o comportamento de construção que pode analisar itens de informações personalizadas e delimitadores personalizados da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0057d-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="0057d-121">Além disso, a cadeia de caracteres de texto à lógica do objeto é potencialmente conversor de tipo de um analisador XAML determinado padrão de nativo para lidar com primitivos que não seja uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0057d-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="0057d-122">O `x:Arguments` uso XAML não é uso do elemento de propriedade no sentido de típico, porque a marcação de diretiva não faz referência a tipo de elemento de objeto recipiente.</span><span class="sxs-lookup"><span data-stu-id="0057d-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="0057d-123">Ele é mais semelhante de outras diretivas como `x:Code` onde o elemento delimita um intervalo no qual a marcação deve ser interpretada como diferente do padrão para o conteúdo filho.</span><span class="sxs-lookup"><span data-stu-id="0057d-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="0057d-124">Nesse caso, o tipo XAML de cada elemento de objeto se comunica informações sobre os tipos de argumento, que são usadas pelo analisadores XAML para determinar qual assinatura do método de fábrica construtor específico um `x:Arguments` uso está tentando fazer referência.</span><span class="sxs-lookup"><span data-stu-id="0057d-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="0057d-125">`x:Arguments` para um elemento de objeto que está sendo construído deve preceder quaisquer outros elementos de propriedade, conteúdo, texto interno ou cadeias de caracteres de inicialização do elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="0057d-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="0057d-126">Os elementos de objeto dentro de `x:Arguments` podem incluir atributos e cadeias de caracteres de inicialização, conforme permitido por esse tipo XAML e seu método de construtor ou fábrica de backup.</span><span class="sxs-lookup"><span data-stu-id="0057d-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="0057d-127">Para o objeto ou os argumentos, você pode especificar os tipos XAML personalizados ou tipos XAML que estariam fora do namespace XAML padrão, fazendo referência a mapeamentos de prefixo estabelecido.</span><span class="sxs-lookup"><span data-stu-id="0057d-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="0057d-128">Processadores XAML usam as diretrizes a seguir para determinar como os argumentos especificados no `x:Arguments` deve ser usado para construir um objeto.</span><span class="sxs-lookup"><span data-stu-id="0057d-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="0057d-129">Se `x:FactoryMethod` for especificado, em comparação com informações especificado `x:FactoryMethod` (Observe que o valor de `x:FactoryMethod` é o nome do método e o método nomeado pode ter sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="0057d-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="0057d-130">Se `x:FactoryMethod` não for especificado, informações é comparado com o conjunto de todas as sobrecargas de construtor público do objeto.</span><span class="sxs-lookup"><span data-stu-id="0057d-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="0057d-131">Lógica de processamento de XAML, em seguida, compara o número de parâmetros e seleciona a sobrecarga com arity correspondente.</span><span class="sxs-lookup"><span data-stu-id="0057d-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="0057d-132">Se houver mais de uma correspondência, o processador XAML deve comparar os tipos dos parâmetros com base nos tipos XAML dos elementos de objeto fornecido.</span><span class="sxs-lookup"><span data-stu-id="0057d-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="0057d-133">Se não houver ainda mais de uma correspondência, o comportamento do processador XAML é indefinido.</span><span class="sxs-lookup"><span data-stu-id="0057d-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="0057d-134">Se um `x:FactoryMethod` for especificado, mas o método não pode ser resolvido, um processador XAML deve lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="0057d-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="0057d-135">Um uso do atributo XAML `<x:Arguments>string</x:Arguments>` é tecnicamente possível.</span><span class="sxs-lookup"><span data-stu-id="0057d-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="0057d-136">No entanto, isso não fornece recursos além do que poderia ser feito caso contrário, por meio de conversores de texto e o tipo de inicialização e usar essa sintaxe não é a intenção de design dos recursos do método de fábrica do XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="0057d-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0057d-137">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0057d-137">Examples</span></span>  
 <span data-ttu-id="0057d-138">O exemplo a seguir mostra um construtor não padrão, assinatura e, em seguida, o uso XAML de `x:Arguments` que acessa essa assinatura.</span><span class="sxs-lookup"><span data-stu-id="0057d-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="0057d-139">O exemplo a seguir mostra uma assinatura de método de fábrica de destino, em seguida, o uso XAML de `x:Arguments` que acessa essa assinatura.</span><span class="sxs-lookup"><span data-stu-id="0057d-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0057d-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0057d-140">See also</span></span>

- [<span data-ttu-id="0057d-141">Definindo tipos personalizados para uso com serviços XAML do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0057d-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="0057d-142">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="0057d-142">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)

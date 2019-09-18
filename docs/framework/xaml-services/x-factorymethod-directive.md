---
title: Diretiva x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053784"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="5374d-102">Diretiva x:FactoryMethod</span><span class="sxs-lookup"><span data-stu-id="5374d-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="5374d-103">Especifica um método diferente de um construtor que um processador XAML deve usar para inicializar um objeto depois de resolver seu tipo de apoio.</span><span class="sxs-lookup"><span data-stu-id="5374d-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="5374d-104">Uso de atributo XAML, sem x:Arguments</span><span class="sxs-lookup"><span data-stu-id="5374d-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="5374d-105">Uso de atributo XAML, x:Arguments como elemento (s)</span><span class="sxs-lookup"><span data-stu-id="5374d-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5374d-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="5374d-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="5374d-107">O nome do método de cadeia de caracteres de um método que os processadores XAML chamam para `object`inicializar a instância especificada como.</span><span class="sxs-lookup"><span data-stu-id="5374d-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="5374d-108">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="5374d-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="5374d-109">Um ou mais elementos de objeto para objetos que especificam parâmetros de método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="5374d-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="5374d-110">A ordem é significativa; significa a ordem na qual os argumentos devem ser passados para o método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="5374d-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5374d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5374d-111">Remarks</span></span>  
 <span data-ttu-id="5374d-112">Se `methodname` for um método de instância, ele não poderá ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="5374d-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="5374d-113">Há suporte para métodos estáticos como métodos de fábrica.</span><span class="sxs-lookup"><span data-stu-id="5374d-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="5374d-114">Se `methodname` é um método estático, `methodname` é fornecido como um *TypeName*. *methodName* a combinação, em que *TypeName* nomeia a classe que define o método de alocador estático.</span><span class="sxs-lookup"><span data-stu-id="5374d-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="5374d-115">*TypeName* pode ser qualificado por prefixo se fizer referência a um tipo em um xmlns mapeado.</span><span class="sxs-lookup"><span data-stu-id="5374d-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="5374d-116">*TypeName* pode ser um tipo diferente de `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="5374d-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="5374d-117">O método de fábrica deve ser um método público declarado do tipo que faz o backup do elemento de objeto relevante.</span><span class="sxs-lookup"><span data-stu-id="5374d-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="5374d-118">O método de fábrica deve retornar uma instância que pode ser atribuída ao objeto relevante.</span><span class="sxs-lookup"><span data-stu-id="5374d-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="5374d-119">Os métodos de fábrica nunca devem retornar NULL.</span><span class="sxs-lookup"><span data-stu-id="5374d-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="5374d-120">`x:Arguments`Opera em um princípio de melhor correspondência para assinaturas de métodos de fábrica.</span><span class="sxs-lookup"><span data-stu-id="5374d-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="5374d-121">A correspondência avalia a contagem de parâmetros primeiro.</span><span class="sxs-lookup"><span data-stu-id="5374d-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="5374d-122">Se houver mais de uma correspondência possível para uma contagem de parâmetros, o tipo de parâmetro será avaliado e a melhor correspondência será determinada.</span><span class="sxs-lookup"><span data-stu-id="5374d-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="5374d-123">Se ainda houver ambigüidade após esta fase de avaliação, o comportamento do processador XAML será indefinido.</span><span class="sxs-lookup"><span data-stu-id="5374d-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="5374d-124">O `x:FactoryMethod` uso do elemento não é o uso do elemento de propriedade no sentido típico, porque a marcação da diretiva não faz referência ao tipo do elemento de objeto recipiente.</span><span class="sxs-lookup"><span data-stu-id="5374d-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="5374d-125">Espera-se que o uso do elemento seja menos comum do que o uso do atributo.</span><span class="sxs-lookup"><span data-stu-id="5374d-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="5374d-126">`x:Arguments`(o atributo ou uso do elemento) pode ser usado junto `x:FactoryMethod` com o uso do elemento, mas isso não é mostrado especificamente nas seções de uso.</span><span class="sxs-lookup"><span data-stu-id="5374d-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="5374d-127">`x:FactoryMethod`como um elemento deve preceder quaisquer outros elementos de propriedade, deve preceder quaisquer `x:Arguments` também fornecidos como elementos e deve preceder qualquer texto de conteúdo/texto interno/inicialização.</span><span class="sxs-lookup"><span data-stu-id="5374d-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5374d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5374d-128">See also</span></span>

- [<span data-ttu-id="5374d-129">Diretiva x:Arguments</span><span class="sxs-lookup"><span data-stu-id="5374d-129">x:Arguments Directive</span></span>](x-arguments-directive.md)

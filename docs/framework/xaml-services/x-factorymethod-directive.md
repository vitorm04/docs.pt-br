---
title: Diretiva x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 2d5656e6328e1902bddcda3d1ac4b4eabb148d28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731355"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="68988-102">Diretiva x:FactoryMethod</span><span class="sxs-lookup"><span data-stu-id="68988-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="68988-103">Especifica um método que não seja um construtor que um processador XAML deve usar para inicializar um objeto depois de resolver o seu tipo de backup.</span><span class="sxs-lookup"><span data-stu-id="68988-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="68988-104">Uso do atributo XAML, não há argumentos de x:</span><span class="sxs-lookup"><span data-stu-id="68988-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="68988-105">Uso do atributo XAML, x: argumentos como elemento (s)</span><span class="sxs-lookup"><span data-stu-id="68988-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="68988-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="68988-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="68988-107">O nome do método de cadeia de caracteres de um método que processadores XAML chamar para inicializar a instância especificada como `object`.</span><span class="sxs-lookup"><span data-stu-id="68988-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="68988-108">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="68988-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="68988-109">Um ou mais elementos de objeto para objetos que especificam parâmetros de método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="68988-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="68988-110">A ordem é significativa; Isso significa que a ordem na qual os argumentos devem ser passados para o método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="68988-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68988-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="68988-111">Remarks</span></span>  
 <span data-ttu-id="68988-112">Se `methodname` é um método de instância, ele não pode ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="68988-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="68988-113">Há suporte para métodos estáticos como métodos de fábrica.</span><span class="sxs-lookup"><span data-stu-id="68988-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="68988-114">Se `methodname` é um método estático, `methodname` é fornecido como um *typeName*. *methodName* combinação, onde *typeName* nomeia a classe que define o método de fábrica estáticos.</span><span class="sxs-lookup"><span data-stu-id="68988-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="68988-115">*typeName* pode ser qualificado prefixo se referindo-se a um tipo em um xmlns mapeado.</span><span class="sxs-lookup"><span data-stu-id="68988-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="68988-116">*typeName* pode ser um tipo diferente `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="68988-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="68988-117">O método de fábrica deve ser um método público declarado do tipo que sustenta o elemento de objeto relevante.</span><span class="sxs-lookup"><span data-stu-id="68988-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="68988-118">O método de fábrica deve retornar uma instância que pode ser atribuído ao objeto relevante.</span><span class="sxs-lookup"><span data-stu-id="68988-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="68988-119">Métodos de fábrica nunca devem retornar nulos.</span><span class="sxs-lookup"><span data-stu-id="68988-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="68988-120">`x:Arguments` opera em um princípio da melhor correspondência para assinaturas de métodos de fábrica.</span><span class="sxs-lookup"><span data-stu-id="68988-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="68988-121">Correspondência avaliará primeiro a contagem de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="68988-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="68988-122">Se houver mais de uma correspondência possível para uma contagem de parâmetros, o tipo de parâmetro é então avaliada e a melhor correspondência é determinada.</span><span class="sxs-lookup"><span data-stu-id="68988-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="68988-123">Se ainda houver ambiguidade depois dessa fase da avaliação, o comportamento do processador XAML será indefinido.</span><span class="sxs-lookup"><span data-stu-id="68988-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="68988-124">O `x:FactoryMethod` uso do elemento não é uso do elemento de propriedade no sentido de típico, porque a marcação de diretiva não faz referência a tipo de elemento de objeto recipiente.</span><span class="sxs-lookup"><span data-stu-id="68988-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="68988-125">Espera-se o uso do elemento é menos comum do que o uso do atributo.</span><span class="sxs-lookup"><span data-stu-id="68988-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="68988-126">`x:Arguments` (uso do atributo ou elemento) pode ser usado junto com `x:FactoryMethod` uso do elemento, mas isso não é especificamente mostrado nas seções de uso.</span><span class="sxs-lookup"><span data-stu-id="68988-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="68988-127">`x:FactoryMethod` como um elemento deve preceder todos os outros elementos de propriedade, devem preceder qualquer `x:Arguments` também fornecidos como elementos e devem preceder qualquer texto de conteúdo/interna/inicialização de texto.</span><span class="sxs-lookup"><span data-stu-id="68988-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68988-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68988-128">See also</span></span>
- [<span data-ttu-id="68988-129">Diretiva x:Arguments</span><span class="sxs-lookup"><span data-stu-id="68988-129">x:Arguments Directive</span></span>](../../../docs/framework/xaml-services/x-arguments-directive.md)

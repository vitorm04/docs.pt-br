---
title: Diretiva x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 8fff4d62e07bdfd4ecc27d2692c391251afdd6d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190685"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="526d6-102">Diretiva x:FactoryMethod</span><span class="sxs-lookup"><span data-stu-id="526d6-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="526d6-103">Especifica um método que não seja um construtor que um processador XAML deve usar para inicializar um objeto depois de resolver o seu tipo de backup.</span><span class="sxs-lookup"><span data-stu-id="526d6-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="526d6-104">Uso do atributo XAML, não há argumentos de x:</span><span class="sxs-lookup"><span data-stu-id="526d6-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="526d6-105">Uso do atributo XAML, x: argumentos como elemento (s)</span><span class="sxs-lookup"><span data-stu-id="526d6-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="526d6-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="526d6-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="526d6-107">O nome do método de cadeia de caracteres de um método que processadores XAML chamar para inicializar a instância especificada como `object`.</span><span class="sxs-lookup"><span data-stu-id="526d6-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="526d6-108">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="526d6-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="526d6-109">Um ou mais elementos de objeto para objetos que especificam parâmetros de método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="526d6-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="526d6-110">A ordem é significativa; Isso significa que a ordem na qual os argumentos devem ser passados para o método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="526d6-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="526d6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="526d6-111">Remarks</span></span>  
 <span data-ttu-id="526d6-112">Se `methodname` é um método de instância, ele não pode ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="526d6-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="526d6-113">Há suporte para métodos estáticos como métodos de fábrica.</span><span class="sxs-lookup"><span data-stu-id="526d6-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="526d6-114">Se `methodname` é um método estático, `methodname` é fornecido como um *typeName*. *methodName* combinação, onde *typeName* nomeia a classe que define o método de fábrica estáticos.</span><span class="sxs-lookup"><span data-stu-id="526d6-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="526d6-115">*typeName* pode ser qualificado prefixo se referindo-se a um tipo em um xmlns mapeado.</span><span class="sxs-lookup"><span data-stu-id="526d6-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="526d6-116">*typeName* pode ser um tipo diferente `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="526d6-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="526d6-117">O método de fábrica deve ser um método público declarado do tipo que sustenta o elemento de objeto relevante.</span><span class="sxs-lookup"><span data-stu-id="526d6-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="526d6-118">O método de fábrica deve retornar uma instância que pode ser atribuído ao objeto relevante.</span><span class="sxs-lookup"><span data-stu-id="526d6-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="526d6-119">Métodos de fábrica nunca devem retornar nulos.</span><span class="sxs-lookup"><span data-stu-id="526d6-119">Factory methods should never return null.</span></span>  
  
 `x:Arguments` <span data-ttu-id="526d6-120">opera em um princípio da melhor correspondência para assinaturas de métodos de fábrica.</span><span class="sxs-lookup"><span data-stu-id="526d6-120">operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="526d6-121">Correspondência avaliará primeiro a contagem de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="526d6-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="526d6-122">Se houver mais de uma correspondência possível para uma contagem de parâmetros, o tipo de parâmetro é então avaliada e a melhor correspondência é determinada.</span><span class="sxs-lookup"><span data-stu-id="526d6-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="526d6-123">Se ainda houver ambiguidade depois dessa fase da avaliação, o comportamento do processador XAML será indefinido.</span><span class="sxs-lookup"><span data-stu-id="526d6-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="526d6-124">O `x:FactoryMethod` uso do elemento não é uso do elemento de propriedade no sentido de típico, porque a marcação de diretiva não faz referência a tipo de elemento de objeto recipiente.</span><span class="sxs-lookup"><span data-stu-id="526d6-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="526d6-125">Espera-se o uso do elemento é menos comum do que o uso do atributo.</span><span class="sxs-lookup"><span data-stu-id="526d6-125">It is expected that element usage is less common than attribute usage.</span></span> `x:Arguments` <span data-ttu-id="526d6-126">(uso do atributo ou elemento) pode ser usado junto com `x:FactoryMethod` uso do elemento, mas isso não é especificamente mostrado nas seções de uso.</span><span class="sxs-lookup"><span data-stu-id="526d6-126">(either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 `x:FactoryMethod` <span data-ttu-id="526d6-127">como um elemento deve preceder todos os outros elementos de propriedade, devem preceder qualquer `x:Arguments` também fornecidos como elementos e devem preceder qualquer texto de conteúdo/interna/inicialização de texto.</span><span class="sxs-lookup"><span data-stu-id="526d6-127">as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526d6-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="526d6-128">See also</span></span>

- [<span data-ttu-id="526d6-129">Diretiva x:Arguments</span><span class="sxs-lookup"><span data-stu-id="526d6-129">x:Arguments Directive</span></span>](x-arguments-directive.md)

---
title: Diretiva x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071531"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="35766-102">Diretiva x:FactoryMethod</span><span class="sxs-lookup"><span data-stu-id="35766-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="35766-103">Especifica um método diferente de um construtor que um processador XAML deve usar para inicializar um objeto depois de resolver seu tipo de backup.</span><span class="sxs-lookup"><span data-stu-id="35766-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="35766-104">Uso de atributo XAML, sem x:Argumentos</span><span class="sxs-lookup"><span data-stu-id="35766-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="35766-105">Uso de atributo XAML, x:Argumentos como Elemento(s)</span><span class="sxs-lookup"><span data-stu-id="35766-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="35766-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="35766-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="35766-107">O nome do método de string de um método que os `object`processadores XAML chamam para inicializar a instância especificada como .</span><span class="sxs-lookup"><span data-stu-id="35766-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="35766-108">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="35766-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="35766-109">Um ou mais elementos de objeto para objetos que especificam parâmetros do método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="35766-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="35766-110">A ordem é significativa; significa a ordem em que os argumentos devem ser passados para o método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="35766-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35766-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="35766-111">Remarks</span></span>  
 <span data-ttu-id="35766-112">Se `methodname` é um método de instância, não pode ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="35766-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="35766-113">Métodos estáticos como métodos de fábrica são suportados.</span><span class="sxs-lookup"><span data-stu-id="35766-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="35766-114">Se `methodname` é um `methodname` método estático, `typeName.methodName` é `typeName` fornecido como uma combinação, onde nomeia a classe que define o método de fábrica estático.</span><span class="sxs-lookup"><span data-stu-id="35766-114">If `methodname` is a static method, `methodname` is provided as a `typeName.methodName` combination, where `typeName` names the class that defines the static factory method.</span></span> <span data-ttu-id="35766-115">`typeName`pode ser qualificado por prefixo se se referir a um tipo em um xmlns mapeado.</span><span class="sxs-lookup"><span data-stu-id="35766-115">`typeName` can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="35766-116">`typeName`pode ser um `typeof(object)`tipo diferente de .</span><span class="sxs-lookup"><span data-stu-id="35766-116">`typeName` can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="35766-117">O método de fábrica deve ser um método público declarado do tipo que apoia o elemento objeto relevante.</span><span class="sxs-lookup"><span data-stu-id="35766-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="35766-118">O método de fábrica deve retornar uma instância que seja atribuída ao objeto relevante.</span><span class="sxs-lookup"><span data-stu-id="35766-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="35766-119">Os métodos de fábrica nunca devem retornar nulos.</span><span class="sxs-lookup"><span data-stu-id="35766-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="35766-120">`x:Arguments`opera em um princípio de melhor correspondência para assinaturas de métodos de fábrica.</span><span class="sxs-lookup"><span data-stu-id="35766-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="35766-121">A correspondência avalia a contagem de parâmetros primeiro.</span><span class="sxs-lookup"><span data-stu-id="35766-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="35766-122">Se houver mais de uma possível correspondência para uma contagem de parâmetros, o tipo de parâmetro é então avaliado e a melhor correspondência é determinada.</span><span class="sxs-lookup"><span data-stu-id="35766-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="35766-123">Se ainda houver ambiguidade após essa fase de avaliação, o comportamento do processador XAML é indefinido.</span><span class="sxs-lookup"><span data-stu-id="35766-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="35766-124">O `x:FactoryMethod` uso do elemento não é o uso do elemento de propriedade no sentido típico, porque a marcação diretiva não faz referência ao tipo do elemento objeto que contém.</span><span class="sxs-lookup"><span data-stu-id="35766-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="35766-125">Espera-se que o uso do elemento seja menos comum do que o uso de atributos.</span><span class="sxs-lookup"><span data-stu-id="35766-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="35766-126">`x:Arguments`(uso de atributo ou elemento) `x:FactoryMethod` pode ser usado juntamente com o uso do elemento, mas isso não é mostrado especificamente nas seções de uso.</span><span class="sxs-lookup"><span data-stu-id="35766-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="35766-127">`x:FactoryMethod`como um elemento deve preceder quaisquer `x:Arguments` outros elementos de propriedade, deve preceder qualquer também fornecido como elementos, e deve preceder qualquer texto/texto interno/inicialização.</span><span class="sxs-lookup"><span data-stu-id="35766-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35766-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="35766-128">See also</span></span>

- [<span data-ttu-id="35766-129">Diretiva x:Arguments</span><span class="sxs-lookup"><span data-stu-id="35766-129">x:Arguments Directive</span></span>](xarguments-directive.md)

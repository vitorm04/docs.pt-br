---
title: Propriedades de Dependência
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: KrzysztofCwalina
ms.openlocfilehash: 52d7a69a3f52c67ebff3f3db1daf0790e995913a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721869"
---
# <a name="dependency-properties"></a><span data-ttu-id="c8ddd-102">Propriedades de Dependência</span><span class="sxs-lookup"><span data-stu-id="c8ddd-102">Dependency Properties</span></span>
<span data-ttu-id="c8ddd-103">Uma propriedade de dependência (DP) é uma propriedade regular que armazena o valor em um repositório de propriedades em vez de armazená-los em uma variável de tipo (campo), por exemplo.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="c8ddd-104">Uma propriedade de dependência anexada é um tipo de propriedade de dependência modelado como métodos Get e Set estáticos que representa "propriedades", que descreve as relações entre objetos e seus contêineres (por exemplo, a posição de um `Button` do objeto em um `Panel` contêiner).</span><span class="sxs-lookup"><span data-stu-id="c8ddd-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="c8ddd-105">**✓ DO** fornecem as propriedades de dependência, se você precisar que as propriedades para oferecer suporte a recursos do WPF, como o estilo, gatilhos, associação de dados, animações, recursos dinâmicos e herança.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="c8ddd-106">Design de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="c8ddd-106">Dependency Property Design</span></span>  
 <span data-ttu-id="c8ddd-107">**✓ DO** herdam <xref:System.Windows.DependencyObject>, ou um de seus subtipos, ao implementar propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="c8ddd-108">O tipo fornece uma implementação muito eficiente de um repositório de propriedades e automaticamente dá suporte à vinculação de dados do WPF.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="c8ddd-109">**✓ DO** fornecem uma propriedade CLR e o campo estático público somente leitura armazenar uma instância de <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> para cada propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="c8ddd-110">**✓ DO** implementar propriedades de dependência chamando métodos de instância <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> e <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c8ddd-111">**✓ DO** nome do campo de propriedade de dependência estática colocando o sufixo do nome da propriedade com "Property".</span><span class="sxs-lookup"><span data-stu-id="c8ddd-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="c8ddd-112">**X DO NOT** definir valores padrão das propriedades de dependência explicitamente no código; defini-las nos metadados.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="c8ddd-113">Se você definir um padrão de propriedade explicitamente, poderá impedir que essa propriedade sendo definida por meios implícitos, como uma definição de estilo.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="c8ddd-114">**X DO NOT** coloque o código nos acessadores de propriedade que não seja o código padrão para acessar o campo estático.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="c8ddd-115">Que um código não será executado se a propriedade é definida por meios implícitos, como um estilo, porque a definição de estilo usa o campo estático diretamente.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="c8ddd-116">**X DO NOT** usar propriedades de dependência para armazenar dados seguros.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="c8ddd-117">Propriedades de dependência até privados podem ser acessadas publicamente.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="c8ddd-118">Design de propriedade de dependência anexada</span><span class="sxs-lookup"><span data-stu-id="c8ddd-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="c8ddd-119">Propriedades de dependência descritas na seção anterior representam propriedades intrínsecas do tipo declarativo; Por exemplo, o `Text` é uma propriedade do `TextButton`, que declara-o.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="c8ddd-120">Um tipo especial de propriedade de dependência é a propriedade de dependência anexada.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="c8ddd-121">Um exemplo clássico de uma propriedade anexada é o <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c8ddd-122">A propriedade representa a posição da coluna do botão (não da grade), mas só é relevante se o botão está contido em uma grade e, portanto, ele é "anexado" a botões por grades.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
```xaml
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 <span data-ttu-id="c8ddd-123">A definição de uma propriedade anexada a aparência principalmente de uma propriedade de dependência normal, exceto que os acessadores são representados por métodos Get e Set estáticos:</span><span class="sxs-lookup"><span data-stu-id="c8ddd-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
```csharp
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a><span data-ttu-id="c8ddd-124">Validação de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="c8ddd-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="c8ddd-125">As propriedades geralmente implementam o que chamamos de validação.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="c8ddd-126">Lógica de validação é executada quando é feita uma tentativa para alterar o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="c8ddd-127">Infelizmente, acessadores de propriedade de dependência não podem conter código de validação arbitrária.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="c8ddd-128">Em vez disso, lógica de validação de propriedade de dependência deve ser especificado durante o registro de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="c8ddd-129">**X DO NOT** colocar a lógica de validação de propriedade de dependência em acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="c8ddd-130">Em vez disso, transmita um retorno de chamada de validação para `DependencyProperty.Register` método.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="c8ddd-131">Notificações de alteração de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="c8ddd-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="c8ddd-132">**X DO NOT** implementar a lógica de notificação de alteração em acessadores de propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="c8ddd-133">Propriedades de dependência têm um recurso de notificações de alterações interno que deve ser usado, fornecendo um retorno de chamada de notificação de alteração para o <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="c8ddd-134">Coerção de valor de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="c8ddd-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="c8ddd-135">Coerção de propriedade ocorre quando o valor fornecido para um setter de propriedade é modificado por setter antes que o armazenamento de propriedades, na verdade, é modificado.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="c8ddd-136">**X DO NOT** implementar a lógica de coerção em acessadores de propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="c8ddd-137">Propriedades de dependência têm um recurso de coerção interna e ele pode ser usado ao fornecer um retorno de chamada de coerção para o `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="c8ddd-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="c8ddd-138">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="c8ddd-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c8ddd-139">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c8ddd-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ddd-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8ddd-140">See also</span></span>

- [<span data-ttu-id="c8ddd-141">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="c8ddd-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c8ddd-142">Padrões comuns de Design</span><span class="sxs-lookup"><span data-stu-id="c8ddd-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)

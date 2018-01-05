---
title: "Propriedades de Dependência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b9e60f3e941dd1d7d89675f4483ae940b039ba10
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dependency-properties"></a><span data-ttu-id="b3c27-102">Propriedades de Dependência</span><span class="sxs-lookup"><span data-stu-id="b3c27-102">Dependency Properties</span></span>
<span data-ttu-id="b3c27-103">Uma propriedade de dependência (DP) é uma propriedade que armazena o valor em um repositório de propriedades em vez de fazê-lo em uma variável de tipo (campo), por exemplo.</span><span class="sxs-lookup"><span data-stu-id="b3c27-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="b3c27-104">Uma propriedade de dependência anexado é um tipo de propriedade de dependência modelada como métodos Get e Set estáticos que representa "propriedades", que descrevem relações entre seus contêineres e objetos (por exemplo, a posição de um `Button` do objeto em um `Panel` contêiner).</span><span class="sxs-lookup"><span data-stu-id="b3c27-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="b3c27-105">**FAZER ✓** fornecem as propriedades de dependência, se você precisar que as propriedades para oferecer suporte a recursos do WPF, como o estilo, gatilhos, associação de dados, animações, recursos dinâmicos e herança.</span><span class="sxs-lookup"><span data-stu-id="b3c27-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="b3c27-106">Design de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="b3c27-106">Dependency Property Design</span></span>  
 <span data-ttu-id="b3c27-107">**FAZER ✓** herdam <xref:System.Windows.DependencyObject>, ou um de seus subtipos, ao implementar propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="b3c27-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="b3c27-108">O tipo fornece uma implementação muito eficiente de um repositório de propriedade e automaticamente dá suporte à associação de dados do WPF.</span><span class="sxs-lookup"><span data-stu-id="b3c27-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="b3c27-109">**FAZER ✓** fornecem uma propriedade CLR e o campo estático público somente leitura armazenar uma instância de <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> para cada propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="b3c27-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="b3c27-110">**FAZER ✓** implementar propriedades de dependência chamando métodos de instância <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> e <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3c27-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b3c27-111">**FAZER ✓** nome do campo de propriedade de dependência estática colocando o sufixo do nome da propriedade com "Property".</span><span class="sxs-lookup"><span data-stu-id="b3c27-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="b3c27-112">**X não** definir valores padrão das propriedades de dependência explicitamente no código; defini-las nos metadados.</span><span class="sxs-lookup"><span data-stu-id="b3c27-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="b3c27-113">Se você definir um padrão de propriedade explicitamente, você pode impedir que essa propriedade sendo definida de alguma maneira implícita, como um estilo.</span><span class="sxs-lookup"><span data-stu-id="b3c27-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="b3c27-114">**X não** coloque o código nos acessadores de propriedade que não seja o código padrão para acessar o campo estático.</span><span class="sxs-lookup"><span data-stu-id="b3c27-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="b3c27-115">Se código não irá executar se a propriedade é definida por meio de implícita, como um estilo, porque o estilo usa o campo estático diretamente.</span><span class="sxs-lookup"><span data-stu-id="b3c27-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="b3c27-116">**X não** usar propriedades de dependência para armazenar dados seguros.</span><span class="sxs-lookup"><span data-stu-id="b3c27-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="b3c27-117">Propriedades de dependência até mesmo podem ser acessadas publicamente.</span><span class="sxs-lookup"><span data-stu-id="b3c27-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="b3c27-118">Design de propriedade de dependência anexado</span><span class="sxs-lookup"><span data-stu-id="b3c27-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="b3c27-119">Propriedades de dependência descritas na seção anterior representam propriedades intrínsecas do tipo de declaração; Por exemplo, o `Text` é uma propriedade do `TextButton`, que declara.</span><span class="sxs-lookup"><span data-stu-id="b3c27-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="b3c27-120">Um tipo especial de propriedade de dependência é a propriedade de dependência anexado.</span><span class="sxs-lookup"><span data-stu-id="b3c27-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="b3c27-121">É um exemplo clássico de uma propriedade anexada a <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b3c27-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b3c27-122">A propriedade representa a posição de coluna do botão (não da grade), mas só será relevante se o botão estiver contido em uma grade e, portanto, é "anexado" a botões pela grade.</span><span class="sxs-lookup"><span data-stu-id="b3c27-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 <span data-ttu-id="b3c27-123">A definição de uma propriedade anexada aparência principalmente de uma propriedade de dependência normal, exceto que os acessadores são representados por métodos estáticos Get e Set:</span><span class="sxs-lookup"><span data-stu-id="b3c27-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
```  
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
  
## <a name="dependency-property-validation"></a><span data-ttu-id="b3c27-124">Validação de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="b3c27-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="b3c27-125">Propriedades geralmente implementam o que é chamado de validação.</span><span class="sxs-lookup"><span data-stu-id="b3c27-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="b3c27-126">Lógica de validação é executada quando é feita uma tentativa de alterar o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="b3c27-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="b3c27-127">Infelizmente acessadores de propriedade de dependência não podem conter código de validação arbitrária.</span><span class="sxs-lookup"><span data-stu-id="b3c27-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="b3c27-128">Em vez disso, lógica de validação de propriedade de dependência deve ser especificado durante o registro de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b3c27-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="b3c27-129">**X não** colocar a lógica de validação de propriedade de dependência em acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b3c27-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="b3c27-130">Em vez disso, passar um retorno de chamada de validação para `DependencyProperty.Register` método.</span><span class="sxs-lookup"><span data-stu-id="b3c27-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="b3c27-131">Notificações de alteração de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="b3c27-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="b3c27-132">**X não** implementar a lógica de notificação de alteração em acessadores de propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="b3c27-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="b3c27-133">Propriedades de dependência tem um recurso de notificações de alteração interna que deve ser usado, fornecendo um retorno de chamada de notificação de alteração para o <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="b3c27-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="b3c27-134">Coerção de valor de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="b3c27-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="b3c27-135">Coerção de propriedade ocorre quando o valor fornecido para um setter de propriedade for modificado pela setter antes que o armazenamento de propriedades, na verdade, é modificado.</span><span class="sxs-lookup"><span data-stu-id="b3c27-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="b3c27-136">**X não** implementar a lógica de coerção em acessadores de propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="b3c27-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="b3c27-137">Propriedades de dependência tem um recurso de coerção interna e ele pode ser usado, fornecendo um retorno de chamada de coerção para o `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="b3c27-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="b3c27-138">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="b3c27-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b3c27-139">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b3c27-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c27-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3c27-140">See Also</span></span>  
 [<span data-ttu-id="b3c27-141">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="b3c27-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b3c27-142">Padrões comuns de Design</span><span class="sxs-lookup"><span data-stu-id="b3c27-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)

---
title: Propriedades de Dependência
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: e1372b75cb6501f8bc3fec913364e9d80157ad83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741727"
---
# <a name="dependency-properties"></a><span data-ttu-id="6a506-102">Propriedades de Dependência</span><span class="sxs-lookup"><span data-stu-id="6a506-102">Dependency Properties</span></span>
<span data-ttu-id="6a506-103">Uma propriedade de dependência (DP) é uma propriedade regular que armazena seu valor em um repositório de propriedades, em vez de armazená-la em uma variável de tipo (campo), por exemplo.</span><span class="sxs-lookup"><span data-stu-id="6a506-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="6a506-104">Uma propriedade de dependência anexada é um tipo de propriedade de dependência modelada como métodos get e Set estáticos que representam "Propriedades", que descreve as relações entre objetos e seus contêineres (por exemplo, a posição de um objeto `Button` em um contêiner `Panel`).</span><span class="sxs-lookup"><span data-stu-id="6a506-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="6a506-105">✔️ fornecer as propriedades de dependência, se você precisar das propriedades para oferecer suporte a recursos do WPF, como estilo, gatilhos, vinculação de dados, animações, recursos dinâmicos e herança.</span><span class="sxs-lookup"><span data-stu-id="6a506-105">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="6a506-106">Design de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="6a506-106">Dependency Property Design</span></span>
 <span data-ttu-id="6a506-107">✔️ herdar de <xref:System.Windows.DependencyObject>, ou de um de seus subtipos, ao implementar propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="6a506-107">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="6a506-108">O tipo fornece uma implementação muito eficiente de um repositório de propriedades e oferece suporte automático à ligação de dados do WPF.</span><span class="sxs-lookup"><span data-stu-id="6a506-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="6a506-109">✔️ fornecem uma propriedade CLR regular e um campo somente leitura estático público que armazena uma instância de <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> para cada propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="6a506-109">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="6a506-110">✔️ implementar propriedades de dependência chamando métodos de instância <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> e <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a506-110">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="6a506-111">✔️ nomear o campo estático da propriedade de dependência, sufixando o nome da propriedade com "Property".</span><span class="sxs-lookup"><span data-stu-id="6a506-111">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="6a506-112">❌ não definir valores padrão de propriedades de dependência explicitamente no código; em vez disso, defina-os nos metadados.</span><span class="sxs-lookup"><span data-stu-id="6a506-112">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="6a506-113">Se você definir uma propriedade padrão explicitamente, poderá impedir que essa propriedade seja definida por alguns meios implícitos, como um estilo.</span><span class="sxs-lookup"><span data-stu-id="6a506-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="6a506-114">❌ não coloque o código nos acessadores de propriedade que não sejam o código padrão para acessar o campo estático.</span><span class="sxs-lookup"><span data-stu-id="6a506-114">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="6a506-115">Esse código não será executado se a propriedade for definida por meios implícitos, como um estilo, porque o estilo usa o campo estático diretamente.</span><span class="sxs-lookup"><span data-stu-id="6a506-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="6a506-116">❌ não use Propriedades de dependência para armazenar dados seguros.</span><span class="sxs-lookup"><span data-stu-id="6a506-116">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="6a506-117">Até mesmo as propriedades de dependência privada podem ser acessadas publicamente.</span><span class="sxs-lookup"><span data-stu-id="6a506-117">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="6a506-118">Design de propriedade de dependência anexada</span><span class="sxs-lookup"><span data-stu-id="6a506-118">Attached Dependency Property Design</span></span>
 <span data-ttu-id="6a506-119">As propriedades de dependência descritas na seção anterior representam propriedades intrínsecas do tipo declarativo; por exemplo, a propriedade `Text` é uma propriedade de `TextButton`, que a declara.</span><span class="sxs-lookup"><span data-stu-id="6a506-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="6a506-120">Um tipo especial de propriedade de dependência é a propriedade de dependência anexada.</span><span class="sxs-lookup"><span data-stu-id="6a506-120">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="6a506-121">Um exemplo clássico de uma propriedade anexada é a propriedade <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a506-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6a506-122">A propriedade representa a posição da coluna do botão (não da grade), mas só será relevante se o botão estiver contido em uma grade e, portanto, "anexado" a botões por grades.</span><span class="sxs-lookup"><span data-stu-id="6a506-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

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

 <span data-ttu-id="6a506-123">A definição de uma propriedade anexada é parecida com a de uma propriedade de dependência regular, exceto que os acessadores são representados pelos métodos get e Set estáticos:</span><span class="sxs-lookup"><span data-stu-id="6a506-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

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

## <a name="dependency-property-validation"></a><span data-ttu-id="6a506-124">Validação de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="6a506-124">Dependency Property Validation</span></span>
 <span data-ttu-id="6a506-125">As propriedades geralmente implementam o que é chamado de validação.</span><span class="sxs-lookup"><span data-stu-id="6a506-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="6a506-126">A lógica de validação é executada quando é feita uma tentativa de alterar o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a506-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="6a506-127">Infelizmente, os acessadores de propriedade de dependência não podem conter código de validação arbitrário.</span><span class="sxs-lookup"><span data-stu-id="6a506-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="6a506-128">Em vez disso, a lógica de validação da propriedade de dependência precisa ser especificada durante o registro da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a506-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="6a506-129">❌ não coloque a lógica de validação da propriedade de dependência nos acessadores da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a506-129">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="6a506-130">Em vez disso, passe um retorno de chamada de validação para `DependencyProperty.Register` método.</span><span class="sxs-lookup"><span data-stu-id="6a506-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="6a506-131">Notificações de alteração de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="6a506-131">Dependency Property Change Notifications</span></span>
 <span data-ttu-id="6a506-132">❌ não implementar a lógica de notificação de alteração em acessadores de propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="6a506-132">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="6a506-133">As propriedades de dependência têm um recurso interno de notificações de alteração que deve ser usado ao fornecer um retorno de chamada de notificação de alteração para o <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="6a506-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="6a506-134">Coerção de valor de propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="6a506-134">Dependency Property Value Coercion</span></span>
 <span data-ttu-id="6a506-135">A coerção de propriedade ocorre quando o valor fornecido a um setter de propriedade é modificado pelo setter antes que o repositório de propriedades seja realmente modificado.</span><span class="sxs-lookup"><span data-stu-id="6a506-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="6a506-136">❌ não implementar a lógica de coerção em acessadores de propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="6a506-136">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="6a506-137">As propriedades de dependência têm um recurso de coerção interno e podem ser usadas fornecendo um retorno de chamada de coerção para o `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="6a506-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="6a506-138">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="6a506-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6a506-139">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6a506-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6a506-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a506-140">See also</span></span>

- [<span data-ttu-id="6a506-141">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="6a506-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="6a506-142">Padrões comuns de Design</span><span class="sxs-lookup"><span data-stu-id="6a506-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)

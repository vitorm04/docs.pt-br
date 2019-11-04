---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 28f3aa500014b768bd07723511613a42df8689aa
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458766"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="28329-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="28329-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="28329-103">Especifica as propriedades de uma fonte de associação de <xref:System.Windows.Data.RelativeSource>, a ser usada em uma [extensão de marcação de associação](binding-markup-extension.md)ou ao definir a propriedade <xref:System.Windows.Data.Binding.RelativeSource%2A> de um elemento <xref:System.Windows.Data.Binding> estabelecido em XAML.</span><span class="sxs-lookup"><span data-stu-id="28329-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="28329-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="28329-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="28329-105">Uso de atributo XAML (aninhado em uma extensão de associação)</span><span class="sxs-lookup"><span data-stu-id="28329-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="28329-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="28329-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="28329-107">\- ou -</span><span class="sxs-lookup"><span data-stu-id="28329-107">-or-</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a><span data-ttu-id="28329-108">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="28329-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="28329-109">Um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="28329-109">One of the following:</span></span><br /><br /> <span data-ttu-id="28329-110">-O token da cadeia de caracteres `Self`; corresponde a um <xref:System.Windows.Data.RelativeSource> criado com sua propriedade <xref:System.Windows.Data.RelativeSource.Mode%2A> definida como <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="28329-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="28329-111">-O token da cadeia de caracteres `TemplatedParent`; corresponde a um <xref:System.Windows.Data.RelativeSource> criado com sua propriedade <xref:System.Windows.Data.RelativeSource.Mode%2A> definida como <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="28329-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="28329-112">-O token da cadeia de caracteres `PreviousData`; corresponde a um <xref:System.Windows.Data.RelativeSource> criado com sua propriedade <xref:System.Windows.Data.RelativeSource.Mode%2A> definida como <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="28329-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="28329-113">– Veja abaixo para obter informações sobre o modo `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="28329-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="28329-114">O token da cadeia de caracteres `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="28329-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="28329-115">Ao usar este token entra-se em um modo por meio do qual `RelativeSource` especifica um tipo de ancestral e opcionalmente um nível de ancestral.</span><span class="sxs-lookup"><span data-stu-id="28329-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="28329-116">Isso corresponde a <xref:System.Windows.Data.RelativeSource>, conforme criado com a propriedade <xref:System.Windows.Data.RelativeSource.Mode%2A>, definida como <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="28329-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="28329-117">Necessário para o modo `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="28329-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="28329-118">O nome de um tipo que preenche a propriedade <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="28329-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="28329-119">Opcional para o modo `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="28329-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="28329-120">Um nível de ancestral (avaliado de acordo com a direção do pai na árvore lógica).</span><span class="sxs-lookup"><span data-stu-id="28329-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="28329-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="28329-121">Remarks</span></span>

<span data-ttu-id="28329-122">Usos de associação `{RelativeSource TemplatedParent}` são técnicas-chave que atendem a um conceito maior de separação de uma interface do usuário do controle e uma lógica do controle.</span><span class="sxs-lookup"><span data-stu-id="28329-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="28329-123">Isso habilita a associação a partir da definição de modelo a um pai modelo (instância do objeto de tempo de execução em que o modelo é aplicado).</span><span class="sxs-lookup"><span data-stu-id="28329-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="28329-124">Nesse caso, a [Extensão de Marcação TemplateBinding](templatebinding-markup-extension.md) é, na verdade, uma abreviação da seguinte expressão de associação: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="28329-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="28329-125">Os usos `TemplateBinding` ou `{RelativeSource TemplatedParent}` são ambos relevantes apenas no XAML que define um modelo.</span><span class="sxs-lookup"><span data-stu-id="28329-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="28329-126">Para obter mais informações, consulte [extensão de marcação TemplateBinding](templatebinding-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="28329-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="28329-127">O `{RelativeSource FindAncestor}` é usado principalmente em modelos de controle ou em composições de interface do usuário independentes previsíveis para casos em que um controle deve estar sempre em uma árvore visual de um determinado tipo de ancestral.</span><span class="sxs-lookup"><span data-stu-id="28329-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="28329-128">Por exemplo, os itens de um controle de itens podem utilizar os usos `FindAncestor` para se associar às propriedades do ancestral pai do controle de itens.</span><span class="sxs-lookup"><span data-stu-id="28329-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="28329-129">Ou, os elementos que fazem parte da composição de controle em um modelo podem usar associações `FindAncestor` para elementos pai na mesma estrutura da composição.</span><span class="sxs-lookup"><span data-stu-id="28329-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="28329-130">Na sintaxe de elemento de objeto do modo `FindAncestor` exibida nas seções de Sintaxe XAML, a segunda sintaxe de elemento de objeto é usada especificamente para o modo `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="28329-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="28329-131">O modo `FindAncestor` requer um valor <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.</span><span class="sxs-lookup"><span data-stu-id="28329-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="28329-132">Você deve definir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> como um atributo usando uma referência de [extensão de marcação x:Type](../../xaml-services/x-type-markup-extension.md) para o tipo de ancestral a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="28329-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="28329-133">O valor <xref:System.Windows.Data.RelativeSource.AncestorType%2A> é usado quando a requisição de associação é processada em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="28329-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="28329-134">Para o modo `FindAncestor`, a propriedade opcional <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> pode ajudar a desambiguar a consulta de ancestral em casos em que exista possivelmente mais de um ancestral daquele tipo na árvore de elemento.</span><span class="sxs-lookup"><span data-stu-id="28329-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="28329-135">Para obter mais informações sobre como usar o modo `FindAncestor`, consulte <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="28329-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="28329-136">`{RelativeSource Self}` é útil para cenários em que uma propriedade de uma instância deve depender do valor de outra propriedade da mesma instância e não existe nenhuma relação geral da propriedade de dependência (como a coerção) entre as duas propriedades.</span><span class="sxs-lookup"><span data-stu-id="28329-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="28329-137">Embora seja raro duas propriedades existirem em um objeto de modo que os valores sejam literalmente idênticos (e tipados de modo idêntica), você também pode aplicar um parâmetro de `Converter` a uma associação que tenha `{RelativeSource Self}` e usar o conversor para converter entre os tipos de origem e de destino.</span><span class="sxs-lookup"><span data-stu-id="28329-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="28329-138">Outro cenário para `{RelativeSource Self}` é como parte de um <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="28329-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="28329-139">Por exemplo, o seguinte XAML define um elemento <xref:System.Windows.Shapes.Rectangle> de modo que não importa qual valor é inserido para <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> sempre será um quadrado: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="28329-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="28329-140">O `{RelativeSource PreviousData}` é útil em modelos de dados ou em casos em que as associações estão usando uma coleção como a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="28329-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="28329-141">Você pode usar `{RelativeSource PreviousData}` para realçar relacionamentos entre itens de dados adjacentes na coleção.</span><span class="sxs-lookup"><span data-stu-id="28329-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="28329-142">Uma técnica relacionada é estabelecer um <xref:System.Windows.Data.MultiBinding> entre os itens atuais e anteriores na fonte de dados, e usar um conversor nessa associação para determinar a diferença entre os dois itens e suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="28329-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="28329-143">No exemplo a seguir, o primeiro <xref:System.Windows.Controls.TextBlock> no modelo de itens exibe o número atual.</span><span class="sxs-lookup"><span data-stu-id="28329-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="28329-144">A segunda <xref:System.Windows.Controls.TextBlock> associação é uma <xref:System.Windows.Data.MultiBinding> que tem, de maneira nominal, dois constituintes de <xref:System.Windows.Data.Binding>: o registro atual e uma associação que usa deliberadamente o registro de dados anterior usando `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="28329-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="28329-145">Em seguida, um conversor em <xref:System.Windows.Data.MultiBinding> calcula a diferença e retorne à associação.</span><span class="sxs-lookup"><span data-stu-id="28329-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
```

<span data-ttu-id="28329-146">A descrição de vinculação de dados como um conceito não é abordado aqui; consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="28329-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="28329-147">Na implementação do processador XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o tratamento para essa extensão de marcação é definido pela classe <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="28329-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="28329-148">`RelativeSource` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="28329-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="28329-149">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="28329-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="28329-150">Todas as extensões de marcação em XAML usam os caracteres `{` e `}` na sintaxe de atributo, que é a convenção pela qual o processador XAML reconhece que uma extensão de marcação precisa processar o atributo.</span><span class="sxs-lookup"><span data-stu-id="28329-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="28329-151">Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="28329-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28329-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28329-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="28329-153">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="28329-153">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="28329-154">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="28329-154">XAML Overview (WPF)</span></span>](xaml-overview-wpf.md)
- [<span data-ttu-id="28329-155">Extensões de marcação e XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="28329-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="28329-156">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="28329-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="28329-157">Visão geral das declarações de associação</span><span class="sxs-lookup"><span data-stu-id="28329-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="28329-158">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="28329-158">x:Type Markup Extension</span></span>](../../xaml-services/x-type-markup-extension.md)

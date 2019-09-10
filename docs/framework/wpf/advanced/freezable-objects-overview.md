---
title: Visão geral de objetos congeláveis
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: 854565e28e646ef57658e2bfdb7326d8453448d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856076"
---
# <a name="freezable-objects-overview"></a>Visão geral de objetos congeláveis

Este tópico descreve como usar e criar <xref:System.Windows.Freezable> objetos com eficiência, que fornecem recursos especiais que podem ajudar a melhorar o desempenho do aplicativo. Exemplos de objetos congeláveis incluem pincéis, canetas, transformações, geometrias e animações.

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a>O que é um Congelável?

Um <xref:System.Windows.Freezable> é um tipo especial de objeto que tem dois Estados: descongelado e congelado. Quando uncongelado, um <xref:System.Windows.Freezable> parece se comportar como qualquer outro objeto. Quando congelado, um <xref:System.Windows.Freezable> não pode mais ser modificado.

Um <xref:System.Windows.Freezable> fornece um <xref:System.Windows.Freezable.Changed> evento para notificar os observadores de quaisquer modificações ao objeto. Congelar um <xref:System.Windows.Freezable> pode melhorar seu desempenho, pois ele não precisa mais gastar recursos em notificações de alteração. Um congelado <xref:System.Windows.Freezable> também pode ser compartilhado entre threads, enquanto um não <xref:System.Windows.Freezable> congelado não pode.

Embora a <xref:System.Windows.Freezable> classe tenha muitos aplicativos, a <xref:System.Windows.Freezable> maioria dos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objetos no está relacionada ao subsistema de gráficos.

A <xref:System.Windows.Freezable> classe facilita o uso de determinados objetos do sistema de gráficos e pode ajudar a melhorar o desempenho do aplicativo. Exemplos de tipos que herdam <xref:System.Windows.Freezable> de incluem <xref:System.Windows.Media.Brush>as <xref:System.Windows.Media.Transform>classes, <xref:System.Windows.Media.Geometry> e. Como eles contêm recursos não gerenciados, o sistema deve monitorar as modificações a esses objetos e, em seguida, atualizar seus recursos não gerenciados correspondentes, quando houver uma alteração no objeto original. Mesmo se você não realmente modificar um objeto do sistema de elementos gráficos, o sistema ainda deverá gastar um pouco de seus recursos monitorando o objeto, para o caso de você alterá-lo.

Por exemplo, suponha que você crie <xref:System.Windows.Media.SolidColorBrush> um pincel e use-o para pintar o plano de fundo de um botão.

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

Quando o botão é renderizado, o subsistema de elementos gráficos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa as informações fornecidas para pintar um grupo de pixels para criar a aparência de um botão. Embora você tenha usado um pincel de cor sólida para descrever como o botão deveria ser pintado, seu pincel de cor sólida, na verdade, não faz a pintura. O sistema de elementos gráficos gera objetos rápidos e de baixo nível para o botão e o pincel e são esses objetos que realmente aparecem na tela.

Se você fosse modificar o pincel, esses objetos de baixo nível precisariam ser regenerados. A classe congelável é o que proporciona a um pincel a capacidade de localizar seus objetos gerados e de nível inferior correspondentes e atualizá-los quando forem alterados. Quando essa capacidade é habilitada, significa que o pincel está "descongelado."

O método de <xref:System.Windows.Freezable.Freeze%2A> um Freezable permite que você desabilite essa capacidade de autoatualização. Você pode usar esse método para fazer com que o pincel se torne "congelado" ou não modificável.

> [!NOTE]
> Nem todo objeto Congelável pode ser congelado. Para evitar lançar um <xref:System.InvalidOperationException>, verifique o valor da Propriedade do <xref:System.Windows.Freezable.CanFreeze%2A> objeto Freezable para determinar se ele pode ser congelado antes de tentar congele-lo.

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

Quando você não precisa mais modificar um congelável, congelá-lo fornece benefícios de desempenho. Se você congelasse o pincel nesse exemplo, o sistema de elementos gráficos não precisaria mais monitorar as alterações feitas nele. O sistema de elementos gráficos também pode fazer outras otimizações, porque sabe que o pincel não será alterado.

> [!NOTE]
> Por conveniência, objetos congeláveis permanecem descongelados, a menos que você explicitamente os congele.

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a>Usando Congeláveis

O uso de um congelável descongelado é como o uso de qualquer outro tipo de objeto. No exemplo a seguir, a cor de um <xref:System.Windows.Media.SolidColorBrush> é alterada de amarelo para vermelho depois de ser usada para pintar o plano de fundo de um botão. O sistema de elementos gráficos funciona nos bastidores para alterar automaticamente o botão de amarelo para vermelho na próxima vez que a tela for atualizada.

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a>Congelando uma congelável

Para tornar um <xref:System.Windows.Freezable> não modificável, você chama seu <xref:System.Windows.Freezable.Freeze%2A> método. Quando você congela um objeto que contém objetos congeláveis, esses objetos também são congelados. Por exemplo, se você congelar um <xref:System.Windows.Media.PathGeometry>, as figuras e os segmentos que ele contém também ficarão congelados.

Um congelável **não** poderá ser congelado se alguma das seguintes condições for verdadeira:

- Ele tem propriedades animadas ou associadas a dados.

- Ele tem propriedades definidas por um recurso dinâmico. (Consulte os [recursos XAML](xaml-resources.md) para obter mais informações sobre recursos dinâmicos).

- Ele contém <xref:System.Windows.Freezable> subobjetos que não podem ser congelados.

Se essas condições forem falsas e você não pretender modificar o <xref:System.Windows.Freezable>, você deverá congelar para obter os benefícios de desempenho descritos anteriormente.

Depois que você chamar o método <xref:System.Windows.Freezable.Freeze%2A> de um Freezable, ele não poderá mais ser modificado. A tentativa de modificar um objeto congelado faz com <xref:System.InvalidOperationException> que um seja gerado. O código a seguir gera uma exceção, pois tenta modificar o pincel depois de ele ter sido congelado.

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

Para evitar lançar essa exceção, você pode usar o <xref:System.Windows.Freezable.IsFrozen%2A> método para determinar se um <xref:System.Windows.Freezable> está congelado.

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

No exemplo de código anterior, foi feita uma cópia modificável de um objeto congelado usando o <xref:System.Windows.Freezable.Clone%2A> método. A próxima seção aborda a clonagem em mais detalhes.

> [!NOTE]
> Como um Freezable congelado não pode ser animado, o sistema de animação criará automaticamente clones modificáveis <xref:System.Windows.Freezable> de objetos congelados quando você tentar animá- <xref:System.Windows.Media.Animation.Storyboard>los com um. Para eliminar a sobrecarga de desempenho causada pela clonagem, deixe um objeto descongelado se você pretende animá-lo. Para obter mais informações sobre animação com storyboards, consulte a [Visão geral de storyboards](../graphics-multimedia/storyboards-overview.md).

### <a name="freezing-from-markup"></a>Congelamento na marcação

Para congelar um <xref:System.Windows.Freezable> objeto declarado na marcação, use o `PresentationOptions:Freeze` atributo. No exemplo a seguir, um <xref:System.Windows.Media.SolidColorBrush> é declarado como um recurso de página e congelado. Em seguida, ele é usado para definir a tela de fundo de um botão.

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

Para usar o atributo `Freeze`, você deve mapear para o namespace de opções de apresentação: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. O `PresentationOptions` é o prefixo recomendado para mapear este namespace:

```
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

Como nem todos os leitores de XAML reconhecem esse atributo, é recomendável que você use o [mc:Ignorable Attribute](mc-ignorable-attribute.md) para marcar o atributo `Presentation:Freeze` como ignorável:

```
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

Para obter mais informações, consulte a página [Atributo mc:Ignorable](mc-ignorable-attribute.md).

### <a name="unfreezing-a-freezable"></a>"Descongelando" um Congelável

Depois de congelado, <xref:System.Windows.Freezable> um nunca pode ser modificado ou descongelado; no entanto, você pode criar um clone não <xref:System.Windows.Freezable.Clone%2A> congelado <xref:System.Windows.Freezable.CloneCurrentValue%2A> usando o método ou.

No exemplo a seguir, a tela de fundo do botão é definida com um pincel e, então, esse pincel é congelado. Uma cópia não congelada é feita do pincel usando o <xref:System.Windows.Freezable.Clone%2A> método. O clone é modificado e usado para alterar a tela de fundo do botão de amarela para vermelha.

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> Independentemente do método de clonagem usado, as animações nunca são copiadas <xref:System.Windows.Freezable>para o novo.

Os <xref:System.Windows.Freezable.Clone%2A> métodos <xref:System.Windows.Freezable.CloneCurrentValue%2A> e produzem cópias profundas do Freezable. Se o congelável contém outros objetos congeláveis congelados, eles também são clonados e tornados modificáveis. Por exemplo, se você clonar um <xref:System.Windows.Media.PathGeometry> congelado para torná-lo modificável, as figuras e os segmentos que ele contém também serão copiados e tornados modificáveis.

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a>Criando sua própria classe Congelável

Uma classe derivada de <xref:System.Windows.Freezable> Obtém os seguintes recursos.

- Estados especiais: um estado somente leitura (congelada) e gravável.

- Segurança de thread: um <xref:System.Windows.Freezable> congelado pode ser compartilhado entre threads.

- Notificação de alteração detalhada: Ao contrário <xref:System.Windows.DependencyObject>de outros s, os objetos Freezable fornecem notificações de alteração quando os valores de subpropriedades são alterados.

- Fácil clonagem: a classe Congelável tem vários métodos já implementados que produzem clones profundos.

Um <xref:System.Windows.Freezable> é um tipo de <xref:System.Windows.DependencyObject>e, portanto, usa o sistema de propriedades de dependência. Suas propriedades de classe não precisam ser Propriedades de dependência, mas o uso de propriedades de dependência reduzirá a quantidade de código que você precisa <xref:System.Windows.Freezable> escrever, pois a classe foi projetada com propriedades de dependência em mente. Para obter mais informações sobre o sistema de propriedade de dependência, consulte o [Visão geral de propriedades de dependência](dependency-properties-overview.md).

Cada <xref:System.Windows.Freezable> subclasse deve substituir o <xref:System.Windows.Freezable.CreateInstanceCore%2A> método. Se sua classe usa as propriedades de dependência para todos os seus dados, você terminou.

Se sua classe contém membros de dados de propriedade que não são de dependência, você também deve substituir os métodos a seguir:

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

Você também deve observar as seguintes regras para o acesso e gravação em membros de dados que não são propriedades de dependência:

- No início de qualquer API que leia membros de dados de propriedade não dependência, chame o <xref:System.Windows.Freezable.ReadPreamble%2A> método.

- No início de qualquer API que grava membros de dados de propriedade de não dependência, chame <xref:System.Windows.Freezable.WritePreamble%2A> o método. (Depois que você tiver <xref:System.Windows.Freezable.WritePreamble%2A> chamado em uma API, não precisará fazer uma chamada adicional para <xref:System.Windows.Freezable.ReadPreamble%2A> se você também ler membros de dados de propriedade não dependência.)

- Chame o <xref:System.Windows.Freezable.WritePostscript%2A> método antes de sair de métodos que gravam em membros de dados de propriedade de não dependência.

Se sua classe contiver membros de dados de propriedade não dependência que <xref:System.Windows.DependencyObject> são objetos, você também deverá chamar <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> o método sempre que alterar um de seus valores, mesmo se você estiver definindo o membro como `null`.

> [!NOTE]
> É muito importante que você comece cada <xref:System.Windows.Freezable> método que substituir por uma chamada para a implementação base.

Para obter um exemplo de uma <xref:System.Windows.Freezable> classe personalizada, consulte o [exemplo animação personalizada](https://go.microsoft.com/fwlink/?LinkID=159981).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Freezable>
- [Exemplo de animação personalizada](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)

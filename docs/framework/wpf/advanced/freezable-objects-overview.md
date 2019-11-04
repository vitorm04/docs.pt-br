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
ms.openlocfilehash: 755240859829042e9790b9c89e47bb7a2013ceef
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460454"
---
# <a name="freezable-objects-overview"></a>Visão geral de objetos congeláveis

Este tópico descreve como usar e criar com eficiência <xref:System.Windows.Freezable> objetos, que fornecem recursos especiais que podem ajudar a melhorar o desempenho do aplicativo. Exemplos de objetos congeláveis incluem pincéis, canetas, transformações, geometrias e animações.

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a>O que é um Congelável?

Uma <xref:System.Windows.Freezable> é um tipo especial de objeto que tem dois Estados: descongelado e congelado. Quando não congelado, um <xref:System.Windows.Freezable> parece se comportar como qualquer outro objeto. Quando congelado, um <xref:System.Windows.Freezable> não pode mais ser modificado.

Uma <xref:System.Windows.Freezable> fornece um evento <xref:System.Windows.Freezable.Changed> para notificar os observadores de quaisquer modificações ao objeto. Congelar um <xref:System.Windows.Freezable> pode melhorar seu desempenho, pois ele não precisa mais gastar recursos em notificações de alteração. Um <xref:System.Windows.Freezable> congelado também pode ser compartilhado entre threads, enquanto um <xref:System.Windows.Freezable> não congelado não pode.

Embora a classe <xref:System.Windows.Freezable> tenha muitos aplicativos, a maioria dos objetos <xref:System.Windows.Freezable> no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] estão relacionados ao subsistema de gráficos.

A classe <xref:System.Windows.Freezable> torna mais fácil usar determinados objetos do sistema de gráficos e pode ajudar a melhorar o desempenho do aplicativo. Exemplos de tipos que herdam de <xref:System.Windows.Freezable> incluem as classes <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>e <xref:System.Windows.Media.Geometry>. Como eles contêm recursos não gerenciados, o sistema deve monitorar as modificações a esses objetos e, em seguida, atualizar seus recursos não gerenciados correspondentes, quando houver uma alteração no objeto original. Mesmo se você não realmente modificar um objeto do sistema de elementos gráficos, o sistema ainda deverá gastar um pouco de seus recursos monitorando o objeto, para o caso de você alterá-lo.

Por exemplo, suponha que você crie um pincel de <xref:System.Windows.Media.SolidColorBrush> e use-o para pintar o plano de fundo de um botão.

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

Quando o botão é renderizado, o subsistema de elementos gráficos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa as informações fornecidas para pintar um grupo de pixels para criar a aparência de um botão. Embora você tenha usado um pincel de cor sólida para descrever como o botão deveria ser pintado, seu pincel de cor sólida, na verdade, não faz a pintura. O sistema de elementos gráficos gera objetos rápidos e de baixo nível para o botão e o pincel e são esses objetos que realmente aparecem na tela.

Se você fosse modificar o pincel, esses objetos de baixo nível precisariam ser regenerados. A classe congelável é o que proporciona a um pincel a capacidade de localizar seus objetos gerados e de nível inferior correspondentes e atualizá-los quando forem alterados. Quando essa capacidade é habilitada, significa que o pincel está "descongelado."

O método <xref:System.Windows.Freezable.Freeze%2A> de um Freezable permite que você desabilite essa capacidade de autoatualização. Você pode usar esse método para fazer com que o pincel se torne "congelado" ou não modificável.

> [!NOTE]
> Nem todo objeto Congelável pode ser congelado. Para evitar lançar um <xref:System.InvalidOperationException>, verifique o valor da propriedade <xref:System.Windows.Freezable.CanFreeze%2A> do objeto Freezable para determinar se ele pode ser congelado antes de tentar congele-lo.

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

Para tornar um <xref:System.Windows.Freezable> não modificável, chame seu método <xref:System.Windows.Freezable.Freeze%2A>. Quando você congela um objeto que contém objetos congeláveis, esses objetos também são congelados. Por exemplo, se você congelar uma <xref:System.Windows.Media.PathGeometry>, as figuras e os segmentos que ela contém também ficarão congelados.

Um congelável **não** poderá ser congelado se alguma das seguintes condições for verdadeira:

- Ele tem propriedades animadas ou associadas a dados.

- Ele tem propriedades definidas por um recurso dinâmico. (Consulte os [recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) para obter mais informações sobre recursos dinâmicos).

- Ele contém <xref:System.Windows.Freezable> subobjetos que não podem ser congelados.

Se essas condições forem falsas e você não pretender modificar o <xref:System.Windows.Freezable>, você deverá congele-lo para obter os benefícios de desempenho descritos anteriormente.

Depois de chamar o método <xref:System.Windows.Freezable.Freeze%2A> de Freezable, ele não poderá mais ser modificado. A tentativa de modificar um objeto congelado faz com que um <xref:System.InvalidOperationException> seja lançado. O código a seguir gera uma exceção, pois tenta modificar o pincel depois de ele ter sido congelado.

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

Para evitar gerar essa exceção, você pode usar o método <xref:System.Windows.Freezable.IsFrozen%2A> para determinar se um <xref:System.Windows.Freezable> está congelado.

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

No exemplo de código anterior, foi feita uma cópia modificável de um objeto congelado usando o método <xref:System.Windows.Freezable.Clone%2A>. A próxima seção aborda a clonagem em mais detalhes.

> [!NOTE]
> Como um Freezable congelado não pode ser animado, o sistema de animação criará automaticamente clones modificáveis de objetos <xref:System.Windows.Freezable> congelado quando você tentar animá-los com um <xref:System.Windows.Media.Animation.Storyboard>. Para eliminar a sobrecarga de desempenho causada pela clonagem, deixe um objeto descongelado se você pretende animá-lo. Para obter mais informações sobre animação com storyboards, consulte a [Visão geral de storyboards](../graphics-multimedia/storyboards-overview.md).

### <a name="freezing-from-markup"></a>Congelamento na marcação

Para congelar um objeto <xref:System.Windows.Freezable> declarado na marcação, use o atributo `PresentationOptions:Freeze`. No exemplo a seguir, um <xref:System.Windows.Media.SolidColorBrush> é declarado como um recurso de página e congelado. Em seguida, ele é usado para definir a tela de fundo de um botão.

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

Para usar o atributo `Freeze`, você deve mapear para o namespace de opções de apresentação: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. O `PresentationOptions` é o prefixo recomendado para mapear este namespace:

```xaml
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

Como nem todos os leitores de XAML reconhecem esse atributo, é recomendável que você use o [mc:Ignorable Attribute](mc-ignorable-attribute.md) para marcar o atributo `Presentation:Freeze` como ignorável:

```xaml
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

Para obter mais informações, consulte a página [Atributo mc:Ignorable](mc-ignorable-attribute.md).

### <a name="unfreezing-a-freezable"></a>"Descongelando" um Congelável

Depois de congelado, uma <xref:System.Windows.Freezable> nunca pode ser modificada ou descongelada; no entanto, você pode criar um clone não congelado usando o método <xref:System.Windows.Freezable.Clone%2A> ou <xref:System.Windows.Freezable.CloneCurrentValue%2A>.

No exemplo a seguir, a tela de fundo do botão é definida com um pincel e, então, esse pincel é congelado. Uma cópia não congelada é feita do pincel usando o método <xref:System.Windows.Freezable.Clone%2A>. O clone é modificado e usado para alterar a tela de fundo do botão de amarela para vermelha.

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> Independentemente do método de clonagem usado, as animações nunca são copiadas para o novo <xref:System.Windows.Freezable>.

Os métodos <xref:System.Windows.Freezable.Clone%2A> e <xref:System.Windows.Freezable.CloneCurrentValue%2A> produzem cópias profundas do Freezable. Se o congelável contém outros objetos congeláveis congelados, eles também são clonados e tornados modificáveis. Por exemplo, se você clonar um <xref:System.Windows.Media.PathGeometry> congelado para torná-lo modificável, as figuras e os segmentos que ele contém também serão copiados e tornados modificáveis.

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a>Criando sua própria classe Congelável

Uma classe derivada de <xref:System.Windows.Freezable> Obtém os recursos a seguir.

- Estados especiais: um estado somente leitura (congelada) e gravável.

- Segurança de thread: uma <xref:System.Windows.Freezable> congelada pode ser compartilhada entre threads.

- Notificação de alteração detalhada: ao contrário de outras <xref:System.Windows.DependencyObject>s, os objetos Freezable fornecem notificações de alteração quando os valores de subpropriedades são alterados.

- Fácil clonagem: a classe Congelável tem vários métodos já implementados que produzem clones profundos.

Um <xref:System.Windows.Freezable> é um tipo de <xref:System.Windows.DependencyObject>e, portanto, usa o sistema de propriedades de dependência. Suas propriedades de classe não precisam ser Propriedades de dependência, mas o uso de propriedades de dependência reduzirá a quantidade de código que você precisa escrever, pois a classe de <xref:System.Windows.Freezable> foi projetada com propriedades de dependência em mente. Para obter mais informações sobre o sistema de propriedade de dependência, consulte o [Visão geral de propriedades de dependência](dependency-properties-overview.md).

Cada subclasse de <xref:System.Windows.Freezable> deve substituir o método <xref:System.Windows.Freezable.CreateInstanceCore%2A>. Se sua classe usa as propriedades de dependência para todos os seus dados, você terminou.

Se sua classe contém membros de dados de propriedade que não são de dependência, você também deve substituir os métodos a seguir:

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

Você também deve observar as seguintes regras para o acesso e gravação em membros de dados que não são propriedades de dependência:

- No início de qualquer API que leia membros de dados de propriedade não dependência, chame o método <xref:System.Windows.Freezable.ReadPreamble%2A>.

- No início de qualquer API que grava membros de dados de propriedade de não dependência, chame o método <xref:System.Windows.Freezable.WritePreamble%2A>. (Depois que você tiver chamado <xref:System.Windows.Freezable.WritePreamble%2A> em uma API, não será necessário fazer uma chamada adicional para <xref:System.Windows.Freezable.ReadPreamble%2A> se você também ler membros de dados de propriedade não dependentes.)

- Chame o método <xref:System.Windows.Freezable.WritePostscript%2A> antes de sair de métodos que gravam em membros de dados de propriedade de não dependência.

Se sua classe contiver membros de dados de propriedade não dependência que são <xref:System.Windows.DependencyObject> objetos, você também deverá chamar o método <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> cada vez que alterar um de seus valores, mesmo se estiver definindo o membro como `null`.

> [!NOTE]
> É muito importante que você comece cada método de <xref:System.Windows.Freezable> que você substituir por uma chamada para a implementação de base.

Para obter um exemplo de uma classe de <xref:System.Windows.Freezable> personalizada, consulte o [exemplo animação personalizada](https://go.microsoft.com/fwlink/?LinkID=159981).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Freezable>
- [Exemplo de animação personalizada](https://go.microsoft.com/fwlink/?LinkID=159981)
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)

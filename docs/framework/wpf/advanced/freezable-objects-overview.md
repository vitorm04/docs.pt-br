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
ms.openlocfilehash: a1006816168e405d0d79786b8430b802f1ec0928
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216627"
---
# <a name="freezable-objects-overview"></a>Visão geral de objetos congeláveis
Este tópico descreve como usar com eficiência e criar <xref:System.Windows.Freezable> objetos, que oferecem recursos especiais que podem ajudar a melhorar o desempenho do aplicativo. Exemplos de objetos congeláveis incluem pincéis, canetas, transformações, geometrias e animações.  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>O que é um Congelável?  
 Um <xref:System.Windows.Freezable> é um tipo especial de objeto que tem dois estados: descongelado e congelado. Quando descongelado, um <xref:System.Windows.Freezable> parece se comportar como qualquer outro objeto. Quando congelado, um <xref:System.Windows.Freezable> não pode mais ser modificado.  
  
 Um <xref:System.Windows.Freezable> fornece um <xref:System.Windows.Freezable.Changed> eventos para notificar observadores de quaisquer modificações ao objeto. Congelando uma <xref:System.Windows.Freezable> pode melhorar seu desempenho, porque ele não precisa mais gastar recursos em notificações de alteração. Um congelado <xref:System.Windows.Freezable> também pode ser compartilhado entre threads, enquanto um descongelado <xref:System.Windows.Freezable> não é possível.  
  
 Embora o <xref:System.Windows.Freezable> classe tem muitos aplicativos, mais <xref:System.Windows.Freezable> objetos em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] relacionados ao subsistema de elementos gráficos.  
  
 O <xref:System.Windows.Freezable> classe torna mais fácil de usar determinados objetos do sistema de elementos gráficos e pode ajudar a melhorar o desempenho do aplicativo. Exemplos de tipos que herdam <xref:System.Windows.Freezable> incluem o <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, e <xref:System.Windows.Media.Geometry> classes. Como eles contêm recursos não gerenciados, o sistema deve monitorar as modificações a esses objetos e, em seguida, atualizar seus recursos não gerenciados correspondentes, quando houver uma alteração no objeto original. Mesmo se você não realmente modificar um objeto do sistema de elementos gráficos, o sistema ainda deverá gastar um pouco de seus recursos monitorando o objeto, para o caso de você alterá-lo.  
  
 Por exemplo, suponha que você crie um <xref:System.Windows.Media.SolidColorBrush> de pincel e usá-lo para pintar a tela de fundo de um botão.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Quando o botão é renderizado, o subsistema de elementos gráficos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa as informações fornecidas para pintar um grupo de pixels para criar a aparência de um botão. Embora você tenha usado um pincel de cor sólida para descrever como o botão deveria ser pintado, seu pincel de cor sólida, na verdade, não faz a pintura. O sistema de elementos gráficos gera objetos rápidos e de baixo nível para o botão e o pincel e são esses objetos que realmente aparecem na tela.  
  
 Se você fosse modificar o pincel, esses objetos de baixo nível precisariam ser regenerados. A classe congelável é o que proporciona a um pincel a capacidade de localizar seus objetos gerados e de nível inferior correspondentes e atualizá-los quando forem alterados. Quando essa capacidade é habilitada, significa que o pincel está "descongelado."  
  
 Um congelável <xref:System.Windows.Freezable.Freeze%2A> método permite que você desative essa capacidade de AutoAtualização. Você pode usar esse método para fazer com que o pincel se torne "congelado" ou não modificável.  
  
> [!NOTE]
>  Nem todo objeto Congelável pode ser congelado. Para evitar lançar uma <xref:System.InvalidOperationException>, verifique o valor do objeto Freezable <xref:System.Windows.Freezable.CanFreeze%2A> propriedade para determinar se ele pode ser congelado antes de tentar congelá-lo.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 Quando você não precisa mais modificar um congelável, congelá-lo fornece benefícios de desempenho. Se você congelasse o pincel nesse exemplo, o sistema de elementos gráficos não precisaria mais monitorar as alterações feitas nele. O sistema de elementos gráficos também pode fazer outras otimizações, porque sabe que o pincel não será alterado.  
  
> [!NOTE]
>  Por conveniência, objetos congeláveis permanecem descongelados, a menos que você explicitamente os congele.  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Usando Congeláveis  
 O uso de um congelável descongelado é como o uso de qualquer outro tipo de objeto. No exemplo a seguir, a cor de um <xref:System.Windows.Media.SolidColorBrush> é alterada de amarelo para vermelho depois que ele é usado para pintar a tela de fundo de um botão. O sistema de elementos gráficos funciona nos bastidores para alterar automaticamente o botão de amarelo para vermelho na próxima vez que a tela for atualizada.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Congelando uma congelável  
 Para fazer uma <xref:System.Windows.Freezable> não modificável, chame seu <xref:System.Windows.Freezable.Freeze%2A> método. Quando você congela um objeto que contém objetos congeláveis, esses objetos também são congelados. Por exemplo, se você congela um <xref:System.Windows.Media.PathGeometry>, as figuras e segmentos que ele contém seriam congelados também.  
  
 Um congelável **não** poderá ser congelado se alguma das seguintes condições for verdadeira:  
  
-   Ele tem propriedades animadas ou associadas a dados.  
  
-   Ele tem propriedades definidas por um recurso dinâmico. (Consulte os [recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) para obter mais informações sobre recursos dinâmicos).  
  
-   Ele contém <xref:System.Windows.Freezable> subobjetos não podem ser congelados.  
  
 Se essas condições forem falsas, e você não pretende modificar o <xref:System.Windows.Freezable>, em seguida, você deverá congelá-lo para obter os benefícios de desempenho descritos anteriormente.  
  
 Depois de chamar um congelável <xref:System.Windows.Freezable.Freeze%2A> método, ele não pode mais ser modificado. A tentativa de modificar um congelado objeto faz com que um <xref:System.InvalidOperationException> seja lançada. O código a seguir gera uma exceção, pois tenta modificar o pincel depois de ele ter sido congelado.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Para evitar lançar essa exceção, você pode usar o <xref:System.Windows.Freezable.IsFrozen%2A> método para determinar se um <xref:System.Windows.Freezable> está congelado.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 No exemplo de código anterior, uma cópia modificável foi feita de um objeto congelado usando o <xref:System.Windows.Freezable.Clone%2A> método. A próxima seção aborda a clonagem em mais detalhes.  
  
 **Observação** porque um congelado freezable não pode ser animado, o sistema de animação criará automaticamente clones modificáveis de congelado <xref:System.Windows.Freezable> objetos quando você tenta animá-los com um <xref:System.Windows.Media.Animation.Storyboard>. Para eliminar a sobrecarga de desempenho causada pela clonagem, deixe um objeto descongelado se você pretende animá-lo. Para obter mais informações sobre animação com storyboards, consulte a [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### <a name="freezing-from-markup"></a>Congelamento na marcação  
 Para congelar um <xref:System.Windows.Freezable> objeto declarado na marcação, você usa o `PresentationOptions:Freeze` atributo. No exemplo a seguir, um <xref:System.Windows.Media.SolidColorBrush> é declarado como um recurso de página e congelado. Em seguida, ele é usado para definir a tela de fundo de um botão.  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Para usar o atributo `Freeze`, você deve mapear para o namespace de opções de apresentação: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. O `PresentationOptions` é o prefixo recomendado para mapear este namespace:  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Como nem todos os leitores de XAML reconhecem esse atributo, é recomendável que você use o [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) para marcar o atributo `Presentation:Freeze` como ignorável:  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Para obter mais informações, consulte a página [Atributo mc:Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).  
  
### <a name="unfreezing-a-freezable"></a>"Descongelando" um Congelável  
 Após congelado, um <xref:System.Windows.Freezable> nunca pode ser modificado ou descongelado; no entanto, você pode criar um clone descongelado usando o <xref:System.Windows.Freezable.Clone%2A> ou <xref:System.Windows.Freezable.CloneCurrentValue%2A> método.  
  
 No exemplo a seguir, a tela de fundo do botão é definida com um pincel e, então, esse pincel é congelado. Uma cópia descongelada é feita do pincel usando o <xref:System.Windows.Freezable.Clone%2A> método. O clone é modificado e usado para alterar a tela de fundo do botão de amarela para vermelha.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Independentemente de qual método de clonagem usar, animações nunca são copiadas para o novo <xref:System.Windows.Freezable>.  
  
 O <xref:System.Windows.Freezable.Clone%2A> e <xref:System.Windows.Freezable.CloneCurrentValue%2A> métodos produzem cópias profundas do congelável. Se o congelável contém outros objetos congeláveis congelados, eles também são clonados e tornados modificáveis. Por exemplo, se você clonar um congelado <xref:System.Windows.Media.PathGeometry> para torná-lo modificável, as figuras e segmentos que ele contém são também copiados e tornados modificáveis.  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Criando sua própria classe Congelável  
 Uma classe que deriva de <xref:System.Windows.Freezable> obtém os recursos a seguir.  
  
-   Estados especiais: um estado somente leitura (congelada) e gravável.  
  
-   Acesso thread-safe: um congelado <xref:System.Windows.Freezable> pode ser compartilhado entre threads.  
  
-   Notificação de alteração detalhada: ao contrário de outras <xref:System.Windows.DependencyObject>s, objetos congeláveis fornecem notificações de alteração quando valores da subpropriedade são alteram.  
  
-   Fácil clonagem: a classe Congelável tem vários métodos já implementados que produzem clones profundos.  
  
 Um <xref:System.Windows.Freezable> é um tipo de <xref:System.Windows.DependencyObject>e, portanto, usa o sistema de propriedade de dependência. As propriedades de classe não precisam ser propriedades de dependência, mas usar as propriedades de dependência reduzirá a quantidade de código que você precisa escrever, porque o <xref:System.Windows.Freezable> classe foi projetada com propriedades de dependência em mente. Para obter mais informações sobre o sistema de propriedade de dependência, consulte o [Visão geral de propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Cada <xref:System.Windows.Freezable> subclasse deve substituir o <xref:System.Windows.Freezable.CreateInstanceCore%2A> método. Se sua classe usa as propriedades de dependência para todos os seus dados, você terminou.  
  
 Se sua classe contém membros de dados de propriedade que não são de dependência, você também deve substituir os métodos a seguir:  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Você também deve observar as seguintes regras para o acesso e gravação em membros de dados que não são propriedades de dependência:  
  
-   No início de qualquer [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] que lê membros de dados de propriedade não são de dependência, chame o <xref:System.Windows.Freezable.ReadPreamble%2A> método.  
  
-   No início de qualquer API que grava os membros de dados de propriedade não são de dependência, chame o <xref:System.Windows.Freezable.WritePreamble%2A> método. (Depois de ter chamado <xref:System.Windows.Freezable.WritePreamble%2A> em um [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], você não precisa fazer uma chamada adicional para <xref:System.Windows.Freezable.ReadPreamble%2A> se você também pode ler membros de dados de propriedade não são de dependência.)  
  
-   Chamar o <xref:System.Windows.Freezable.WritePostscript%2A> método antes de sair de métodos que gravam em membros de dados de propriedade não são de dependência.  
  
 Se sua classe contém os membros de dados de propriedade de dependência não são <xref:System.Windows.DependencyObject> objetos, você também deve chamar o <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> método cada vez que fizer alterações em seus valores, mesmo se você estiver configurando o membro `null`.  
  
> [!NOTE]
>  É muito importante que você comece cada <xref:System.Windows.Freezable> método substituir com uma chamada para a implementação base.  
  
 Para obter um exemplo de um personalizado <xref:System.Windows.Freezable> classe, consulte a [amostra de animação personalizada](https://go.microsoft.com/fwlink/?LinkID=159981).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Freezable>  
 [Exemplo de animação personalizada](https://go.microsoft.com/fwlink/?LinkID=159981)  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Propriedades de dependência personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)

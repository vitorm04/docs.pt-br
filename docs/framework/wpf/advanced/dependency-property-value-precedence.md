---
title: Precedência do valor de propriedade da dependência
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 178145b06cb937fb677b8454357bed774ed3003b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740853"
---
# <a name="dependency-property-value-precedence"></a>Precedência do valor de propriedade da dependência
<a name="introduction"></a> Este tópico explica como o funcionamento do sistema de propriedades do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode afetar o valor de uma propriedade de dependência e descreve a precedência pela qual os aspectos do sistema de propriedades são aplicados ao valor efetivo de uma propriedade.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Este tópico pressupõe que você entenda as propriedades de dependência da perspectiva de um consumidor das propriedades de dependência existentes em classes do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e que leu [Visão geral das propriedades de dependência](dependency-properties-overview.md). Para seguir os exemplos deste tópico, você também deve ter noções básicas de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e saber como escrever aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>O sistema de propriedades do WPF  
 O sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece uma maneira sofisticada de determinar o valor das propriedades de dependência por uma variedade de fatores, permitindo recursos como validação de propriedade em tempo real, associação tardia e notificação das propriedades relacionadas de alterações nos valores de outras propriedades. A ordem exata e a lógica que é usada para determinar os valores das propriedades de dependência são razoavelmente complexas. Conhecer essa ordem ajudará você a evitar a configuração desnecessária de propriedades e pode também esclarecer dúvidas sobre o motivo exato pelo qual uma tentativa de influenciar ou antecipar um valor da propriedade de dependência não resultou no valor esperado.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Propriedades de dependência podem ser “definidas” em vários locais  
 O exemplo a seguir é [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em que a mesma propriedade (<xref:System.Windows.Controls.Control.Background%2A>) tem três operações "set" diferentes que podem influenciar o valor.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Aqui, qual cor você espera que seja aplicada – vermelho, verde ou azul?  
  
 Com exceção dos valores animados e da coerção, os conjuntos de propriedades locais são definidos com a precedência mais alta. Se você definir um valor localmente, poderá esperar que ele seja respeitado, até mesmo acima de todos os estilos ou modelos de controle. Aqui, no exemplo, <xref:System.Windows.Controls.Control.Background%2A> é definido como vermelho localmente. Portanto, o estilo definido nesse escopo, mesmo que seja um estilo implícito que, caso contrário, se aplique a todos os elementos desse tipo nesse escopo, não é a precedência mais alta para dar a propriedade <xref:System.Windows.Controls.Control.Background%2A> seu valor.  Se você removeu o valor Vermelho local da instância Botão, o estilo terá precedência e o botão obterá o valor Tela de Fundo do estilo.  No estilo, os gatilhos têm precedência e, portanto, o botão será azul se o mouse estiver sobre ele; caso contrário, será verde.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Lista de precedências de configuração das propriedades de dependência  
 Veja a seguir a ordem definitiva que o sistema de propriedades usa ao atribuir os valores de tempo de execução das propriedades de dependência. A precedência mais alta é listada primeiro. Essa lista se expande em algumas das generalizações feitas na [Visão geral das propriedades de dependência](dependency-properties-overview.md).  
  
1. **Coerção do sistema de propriedades.** Para obter detalhes sobre coerção, consulte [Coerção, animação e valor base](#animations) mais adiante neste tópico.  
  
2. **Animações ativas ou animações com um comportamento Em Espera.** Para obter um efeito prático, uma animação de uma propriedade deve conseguir ter precedência sobre o valor base (não animado), mesmo que esse valor tenha sido definido localmente. Para obter detalhes, consulte [Coerção, animação e valor base](#animations) mais adiante neste tópico.  
  
3. **Valor local.** Um valor local pode ser definido por meio da conveniência da propriedade "wrapper", que também equivale a definir como um elemento de propriedade ou atributo em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ou por uma chamada para a API de <xref:System.Windows.DependencyObject.SetValue%2A> usando uma propriedade de uma instância específica. Se você definir um valor local usando uma associação ou um recurso, cada um deles atuará na precedência como se um valor direto fosse definido.  
  
4. **Propriedades de modelo TemplatedParent.** Um elemento tem um <xref:System.Windows.FrameworkElement.TemplatedParent%2A> se ele foi criado como parte de um modelo (um <xref:System.Windows.Controls.ControlTemplate> ou <xref:System.Windows.DataTemplate>). Para obter detalhes sobre quando isso se aplica, consulte [TemplatedParent](#templatedparent) mais adiante neste tópico. No modelo, a seguinte precedência se aplica:  
  
    1. Gatilhos do modelo de <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
    2. Conjuntos de Propriedades (normalmente por meio de atributos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) no modelo de <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
5. **Estilo implícito.** Aplicável somente à propriedade `Style`. A propriedade `Style` é preenchida por qualquer recurso de estilo com uma chave que corresponde ao tipo desse elemento. Esse recurso de estilo deve existir na página ou no aplicativo; a pesquisa de um recurso de estilo implícito não continua nos temas.  
  
6. **Gatilhos de estilo.** Os gatilhos em estilos da página ou do aplicativo (esses estilos podem ser estilos explícitos ou implícitos, mas não baseados em estilos padrão, que têm precedência mais baixa).  
  
7. **Gatilhos de modelo.** Qualquer gatilho de um modelo em um estilo ou um modelo aplicado diretamente.  
  
8. **Setters de estilo.** Valores de um <xref:System.Windows.Setter> em estilos de página ou aplicativo.  
  
9. **Estilo (tema) padrão.** Para obter detalhes sobre quando isso se aplica e como os estilos de tema se relacionam com os modelos nos estilos de tema, consulte [Estilos (tema) padrão](#themestyles) mais adiante neste tópico. Em um estilo padrão, a seguinte ordem de precedência se aplica:  
  
    1. Gatilhos ativos no estilo de tema.  
  
    2. Setters no estilo de tema.  
  
10. **Herança.** Algumas propriedades de dependência herdam seus valores do elemento pai para os elementos filho, de modo que elas não precisam ser definidas especificamente em cada elemento em todo o aplicativo. Para obter detalhes, consulte [Herança do valor da propriedade](property-value-inheritance.md).  
  
11. **Valor padrão dos metadados de propriedades de dependência.** Uma propriedade de dependência específica pode ter um valor padrão, conforme estabelecido pelo registro do sistema de propriedades dessa propriedade específica. Além disso, as classes derivadas que herdam uma propriedade de dependência têm a opção de substituir esses metadados (incluindo o valor padrão) por tipo. Consulte [Metadados de propriedades de dependência](dependency-property-metadata.md) para obter mais informações. Como a herança é verificada antes do valor padrão em uma propriedade herdada, o valor padrão de um elemento pai tem precedência sobre um elemento filho.  Consequentemente, se uma propriedade herdável não for definida em nenhum lugar, o valor padrão especificado na raiz ou no pai será usado em vez do valor padrão do elemento filho.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent como um item de precedência não se aplica a nenhuma propriedade de um elemento declarado diretamente na marcação de aplicativo padrão. O conceito de TemplatedParent existe somente para itens filho em uma árvore visual que passa a existir por meio da aplicação do modelo. Quando o sistema de propriedades pesquisa o modelo de <xref:System.Windows.FrameworkElement.TemplatedParent%2A> em busca de um valor, ele está pesquisando o modelo que criou esse elemento. Os valores de Propriedade do modelo de <xref:System.Windows.FrameworkElement.TemplatedParent%2A> geralmente agem como se fossem definidos como um valor local no elemento filho, mas essa menor precedência versus o valor local existe porque os modelos são potencialmente compartilhados. Para obter detalhes, consulte <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>A propriedade de estilo  
 A ordem de pesquisa descrita anteriormente se aplica a todas as propriedades de dependência possíveis, exceto uma: a propriedade <xref:System.Windows.FrameworkElement.Style%2A>. A propriedade <xref:System.Windows.FrameworkElement.Style%2A> é exclusiva, pois ela não pode ser estilizada, portanto, os itens de precedência 5 a 8 não se aplicam. Além disso, a animação ou a coerção de <xref:System.Windows.FrameworkElement.Style%2A> não é recomendável (e a animação <xref:System.Windows.FrameworkElement.Style%2A> exigiria uma classe de animação personalizada). Isso deixa três maneiras que a propriedade <xref:System.Windows.FrameworkElement.Style%2A> pode ser definida:  
  
- **Estilo explícito.** A propriedade <xref:System.Windows.FrameworkElement.Style%2A> é definida diretamente. Na maioria dos cenários, o estilo não é definido embutido, mas referenciado como um recurso, por chave explícita. Nesse caso, a própria propriedade Estilo atua como se fosse um valor local, conforme o item de precedência 3.  
  
- **Estilo implícito.** A propriedade <xref:System.Windows.FrameworkElement.Style%2A> não está definida diretamente. No entanto, o <xref:System.Windows.FrameworkElement.Style%2A> existe em algum nível na sequência de pesquisa de recursos (página, aplicativo) e é com chave usando uma chave de recurso que corresponde ao tipo ao qual o estilo deve ser aplicado. Nesse caso, a propriedade <xref:System.Windows.FrameworkElement.Style%2A> em si age por uma precedência identificada na sequência como item 5. Essa condição pode ser detectada usando <xref:System.Windows.DependencyPropertyHelper> na propriedade <xref:System.Windows.FrameworkElement.Style%2A> e procurando <xref:System.Windows.BaseValueSource.ImplicitStyleReference> nos resultados.  
  
- **Estilo padrão**, também conhecido como **estilo de tema.** A propriedade <xref:System.Windows.FrameworkElement.Style%2A> não é definida diretamente e, na verdade, será lida como `null` até o tempo de execução. Nesse caso, o estilo é obtido da avaliação de tema em tempo de execução que faz parte do mecanismo de apresentação do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Para estilos implícitos que não estão em temas, o tipo deve corresponder exatamente a `MyButton` classe derivada de `Button`não usará implicitamente um estilo para `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Estilos (tema) padrão  
 Cada controle que acompanha o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem um estilo padrão. Potencialmente, esse estilo padrão varia por tema, razão pela qual ele é, às vezes, conhecido como um estilo de tema.  
  
 As informações mais importantes encontradas em um estilo padrão para um controle são seu modelo de controle, que existe no estilo de tema como um setter para sua propriedade <xref:System.Windows.Controls.Control.Template%2A>. Se não houvesse nenhum modelo dos estilos padrão, um controle sem um modelo personalizado como parte de um estilo personalizado não teria nenhuma aparência visual. O modelo do estilo padrão fornece à aparência visual de cada controle uma estrutura básica e também define as conexões entre as propriedades definidas na árvore visual do modelo e a classe de controle correspondente. Cada controle expõe um conjunto de propriedades que pode influenciar a aparência visual do controle sem substituir o modelo por completo. Por exemplo, considere a aparência visual padrão de um controle de <xref:System.Windows.Controls.Primitives.Thumb>, que é um componente de um <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 Um <xref:System.Windows.Controls.Primitives.Thumb> tem determinadas propriedades personalizáveis. O modelo padrão de uma <xref:System.Windows.Controls.Primitives.Thumb> cria uma estrutura básica/árvore visual com vários componentes <xref:System.Windows.Controls.Border> aninhados para criar uma aparência de bisel. Se uma propriedade que faz parte do modelo for destinada a ser exposta para personalização pela classe <xref:System.Windows.Controls.Primitives.Thumb>, essa propriedade deverá ser exposta por um [TemplateBinding](templatebinding-markup-extension.md)dentro do modelo. No caso de <xref:System.Windows.Controls.Primitives.Thumb>, várias propriedades dessas bordas compartilham uma associação de modelo com propriedades como <xref:System.Windows.Controls.Border.Background%2A> ou <xref:System.Windows.Controls.Border.BorderThickness%2A>. Porém, algumas outras propriedades ou disposições visuais são embutidas em código no modelo de controle ou são associadas a valores obtidos diretamente do tema e não podem ser alteradas sem que seja necessário substituir o modelo inteiro. Em geral, se uma propriedade é obtida de um pai modelo e não é exposta por uma associação de modelo, ela não pode ser ajustada por estilos, pois não há nenhuma maneira fácil de direcioná-la. Porém, essa propriedade ainda poderá ser influenciada pela herança do valor da propriedade no modelo aplicado ou pelo valor padrão.  
  
 Os estilos de tema usam um tipo como a chave em suas definições. No entanto, quando os temas são aplicados a uma determinada instância de elemento, a pesquisa de temas para esse tipo é realizada verificando a propriedade <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> em um controle. Isso é diferente de usar o Tipo literal, como os estilos implícitos usam. O valor de <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> herdaria para classes derivadas, mesmo se o implementador não o tiver alterado (a maneira desejada de alterar a propriedade não é substituí-la no nível de propriedade, mas, em vez disso, alterar seu valor padrão nos metadados da propriedade). Essa indireção permite que as classes base definam os estilos de tema para elementos derivados que, de outro modo, não têm um estilo (ou mais importante, não tem um modelo dentro desse estilo e, portanto, não têm nenhuma aparência visual padrão). Assim, você pode derivar `MyButton` de <xref:System.Windows.Controls.Button> e ainda obterá o modelo de <xref:System.Windows.Controls.Button> padrão. Se você fosse o autor do controle de `MyButton` e quisesse um comportamento diferente, poderia substituir os metadados de propriedade de dependência de <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> em `MyButton` para retornar uma chave diferente e, em seguida, definir os estilos de tema relevantes, incluindo o modelo para `MyButton` Você deve empacotar com seu controle de `MyButton`. Para obter mais detalhes sobre temas, estilos e criação de controle, consulte [Visão geral da criação de controle](../controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Referências a recursos dinâmicos e associação  
 Referências a recursos dinâmicos e operações de associação respeitam a precedência da localização na qual estão definidas. Por exemplo, um recurso dinâmico aplicado a um valor local atua de acordo com o item de precedência 3, uma associação de um setter de propriedade em um estilo de tema é aplicada no item de precedência 9 e assim por diante. Como as referências a recursos dinâmicos e a associação devem poder obter valores do estado de tempo de execução do aplicativo, isso implica que o processo real de determinação da precedência do valor da propriedade específica se estende para o tempo de execução também.  
  
 Estritamente falando, as referências a recursos dinâmicos não fazem parte do sistema de propriedades, mas têm uma própria ordem de pesquisa que interage com a sequência listada acima. Essa precedência é documentada mais detalhadamente em [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md). O resumo básico dessa precedência é: elemento na raiz da página, aplicativo, tema e sistema.  
  
 Os recursos dinâmicos e as associações têm a precedência da localização na qual foram definidas, mas o valor é adiado. Uma consequência disso é que, se você definir um recurso dinâmico ou uma associação com um valor local, uma alteração no valor local substituirá o recurso dinâmico ou a associação por completo. Mesmo que você chame o método <xref:System.Windows.DependencyObject.ClearValue%2A> para limpar o valor definido localmente, o recurso dinâmico ou a associação não será restaurada. Na verdade, se você chamar <xref:System.Windows.DependencyObject.ClearValue%2A> em uma propriedade que tem um recurso dinâmico ou associação em vigor (sem valor local literal), elas serão limpas pela chamada de <xref:System.Windows.DependencyObject.ClearValue%2A> também.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 O método <xref:System.Windows.DependencyObject.SetCurrentValue%2A> é outra maneira de definir uma propriedade, mas não está na ordem de precedência. Em vez disso, <xref:System.Windows.DependencyObject.SetCurrentValue%2A> permite que você altere o valor de uma propriedade sem substituir a origem de um valor anterior. Você pode usar <xref:System.Windows.DependencyObject.SetCurrentValue%2A> sempre que desejar definir um valor sem dar a esse valor a precedência de um valor local. Por exemplo, se uma propriedade for definida por um gatilho e, em seguida, atribuída a outro valor por meio de <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, o sistema de propriedades ainda respeitará o gatilho e a propriedade será alterada se a ação do gatilho ocorrer. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> permite que você altere o valor da propriedade sem dar a ela uma fonte com precedência mais alta. Da mesma forma, você pode usar <xref:System.Windows.DependencyObject.SetCurrentValue%2A> para alterar o valor de uma propriedade sem substituir uma associação.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Coerção, animações e valor base  
 A coerção e a animação agem em um valor que é chamado de "valor base" em todo esse SDK. O valor base é, portanto, qualquer valor determinado por meio da avaliação ascendente de itens até chegar ao item 2.  
  
 Para uma animação, o valor base pode ter um efeito sobre o valor animado, caso essa animação não especifique “De” e “Para” para alguns comportamentos ou caso a animação seja revertida deliberadamente para o valor base quando concluída. Para ver isso na prática, execute a [Amostra de valores de destino De, Para e Por da animação](https://go.microsoft.com/fwlink/?LinkID=159988). Tente definir os valores locais da altura do retângulo no exemplo, para que o valor local inicial seja diferente de qualquer “De” na animação. Você observará que as animações são iniciadas imediatamente usando os valores de “De” e substituem o valor base depois de iniciadas. A animação pode especificar para retornar ao valor encontrado antes da animação quando ela for concluída, especificando o <xref:System.Windows.Media.Animation.FillBehavior>de interrupção. Posteriormente, a precedência normal é usada para a determinação do valor base.  
  
 Várias animações podem ser aplicadas a uma única propriedade, em que cada uma dessas animações possivelmente foi definida em diferentes pontos na precedência de valor. No entanto, potencialmente, essas animações compõem seus valores, em vez de apenas aplicar a animação da precedência mais alta. Isso depende de como exatamente as animações são definidas e do tipo do valor que está sendo animado. Para obter mais informações sobre propriedades de animação, consulte [Visão geral da animação](../graphics-multimedia/animation-overview.md).  
  
 A coerção é aplicada no nível mais alto de todos. Mesmo uma animação já em execução está sujeita à coerção de valor. Algumas propriedades de dependência existentes no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm coerção interna. Para uma propriedade de dependência personalizada, você define o comportamento de coerção para uma propriedade de dependência personalizada escrevendo um <xref:System.Windows.CoerceValueCallback> e passando o retorno de chamada como parte dos metadados quando você cria a propriedade. Também é possível substituir o comportamento de coerção das propriedades existentes substituindo os metadados dessa propriedade em uma classe derivada. A coerção interage com o valor base de tal forma que as restrições na coerção são aplicadas com as restrições existentes no momento, mas o valor base ainda é retido. Portanto, se as restrições na coerção forem retiradas posteriormente, a coerção retornará o valor mais próximo possível do valor base e, potencialmente, a influência de coerção em uma propriedade deixará de existir assim que todas as restrições forem retiradas. Para obter mais informações sobre o comportamento de coerção, consulte [Retornos de chamada da propriedade de dependência e validação](dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Comportamentos de gatilho  
 Em geral, os controles definem os comportamentos de gatilho como parte de seu estilo padrão em temas. A configuração de propriedades locais nos controles pode impedir que os gatilhos possam responder a eventos controlados pelo usuário de maneira visual ou comportamental. O uso mais comum de um gatilho de propriedade é para propriedades de controle ou estado, como <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Por exemplo, por padrão, quando um <xref:System.Windows.Controls.Button> está desabilitado (o gatilho para <xref:System.Windows.UIElement.IsEnabled%2A> é `false`), o valor de <xref:System.Windows.Controls.Control.Foreground%2A> no estilo de tema é o que faz com que o controle apareça "esmaecido". Mas se você tiver definido um valor de <xref:System.Windows.Controls.Control.Foreground%2A> local, essa cor de cinza normal será anulada em precedência pelo conjunto de propriedades local, mesmo nesse cenário disparado por propriedade. Seja cuidadoso ao definir valores para propriedades que têm comportamentos de gatilho no nível de tema e garanta que você não está interferindo impropriamente na experiência do usuário pretendida para o controle.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue e precedência de valor  
 O método <xref:System.Windows.DependencyObject.ClearValue%2A> fornece um meio conveniente para limpar qualquer valor aplicado localmente de uma propriedade de dependência que é definida em um elemento. No entanto, chamar <xref:System.Windows.DependencyObject.ClearValue%2A> não é uma garantia de que o padrão conforme estabelecido nos metadados durante o registro da propriedade é o novo valor efetivo. Todos os outros participantes na precedência de valor ainda estão ativos. Somente o valor definido localmente foi removido da sequência de precedência. Por exemplo, se você chamar <xref:System.Windows.DependencyObject.ClearValue%2A> em uma propriedade em que essa propriedade também é definida por um estilo de tema, o valor do tema será aplicado como o novo valor em vez do padrão baseado em metadados. Se você quiser pegar todos os participantes do valor da Propriedade do processo e definir o valor para o padrão de metadados registrado, poderá obter esse valor padrão de acordo consultando os metadados da propriedade de dependência e, em seguida, poderá usar o valor padrão para localmente Defina a propriedade com uma chamada para <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Retornos de chamada da propriedade de dependência e validação](dependency-property-callbacks-and-validation.md)

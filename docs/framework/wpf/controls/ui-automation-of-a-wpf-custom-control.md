---
title: Automação de UI de um controle personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: 97db94215220ac2a68e0395bd63b7a874a745a48
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243239"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automação de interface do usuário de um controle personalizado do WPF
O [!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] fornece uma interface única e generalizada que os clientes de automação podem usar para examinar ou operar as interfaces do usuário de uma variedade de plataformas e estruturas. O [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] permite que o código de controle de qualidade (teste) e os aplicativos de acessibilidade, como leitores de tela, examinem os elementos de interface do usuário e simulem a interação do usuário com eles em outro código. Para obter informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] em todas as plataformas, consulte Acessibilidade.  
  
 Este tópico descreve como implementar um provedor da Automação da Interface do Usuário do lado do servidor para um controle personalizado que é executado em um aplicativo WPF. O WPF dá suporte ao [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] por meio de uma árvore de objetos pares de automação que se coloca em paralelo com a árvore de elementos de interface do usuário. O código de teste e os aplicativos que fornecem recursos de acessibilidade podem usar objetos pares de automação diretamente (para código em processo) ou por meio da interface generalizada fornecida pelo [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  

<a name="AutomationPeerClasses"></a>
## <a name="automation-peer-classes"></a>Classes par de automação  
 O WPF [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] controla o suporte através <xref:System.Windows.Automation.Peers.AutomationPeer>de uma árvore de classes de pares que derivam de . Por convenção, os nomes de classe pares começam com o nome de classe do controle e terminam com "AutomationPeer". Por exemplo, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> é a <xref:System.Windows.Controls.Button> classe de pares para a classe de controle. As classes de pares [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] são aproximadamente equivalentes aos tipos de controle, mas são específicas para elementos WPF. O código de automação que acessa aplicativos WPF por meio da interface de [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] não usa pares de automação diretamente, mas o código de automação no mesmo espaço de processo pode usar pares de automação diretamente.  
  
<a name="BuiltInAutomationPeerClasses"></a>
## <a name="built-in-automation-peer-classes"></a>Classes pares de automação internas  
 Os elementos implementam uma classe par de automação se aceitam atividade proveniente da interface do usuário ou se contêm informações necessárias aos usuários de aplicativos de leitor de tela. Nem todos os elementos visuais do WPF têm pares de automação. Exemplos de classes que implementam <xref:System.Windows.Controls.TextBox>pares <xref:System.Windows.Controls.Label>de automação são, <xref:System.Windows.Controls.Button>e . Exemplos de classes que não implementam pares <xref:System.Windows.Controls.Decorator>de automação <xref:System.Windows.Controls.Border>são classes <xref:System.Windows.Controls.Panel>que derivam, como , e classes baseadas em, como <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Controls.Canvas>.  
  
 A <xref:System.Windows.Controls.Control> classe base não tem uma classe de pares correspondente. Se você precisar de uma classe de pares <xref:System.Windows.Controls.Control>para corresponder a um controle <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>personalizado que deriva, você deve derivar a classe de pares personalizadode .  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations-for-derived-peers"></a>Considerações de segurança para pares derivados  
 Os pares de automação devem ser executados em um ambiente de confiança parcial. O código no assembly UIAutomationClient não está configurado para ser executado em um ambiente de confiança parcial e o código par de automação não deve fazer referência a esse assembly. Em vez disso, você deve usar as classes no assembly UIAutomationTypes. Por exemplo, você <xref:System.Windows.Automation.AutomationElementIdentifiers> deve usar a classe do conjunto UIAutomationTypes, que corresponde à <xref:System.Windows.Automation.AutomationElement> classe no conjunto UIAutomationClient. É seguro fazer referência ao assembly UIAutomationTypes no código par de automação.  
  
<a name="PeerNavigation"></a>
## <a name="peer-navigation"></a>Navegação par  
 Depois de localizar um peer de automação, o código no processo <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> pode navegar na árvore de pares chamando os métodos e métodos do objeto. A navegação entre os elementos wpf dentro de um <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> controle é apoiada pela implementação do método pelo par. O sistema de Automação da Interface do Usuário chama esse método para compilar uma árvore de subelementos contidos em um controle, por exemplo, itens de lista em uma caixa de listagem. O <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> método padrão atravessa a árvore visual dos elementos para construir a árvore dos pares de automação. Os controles personalizados substituem esse método para expor elementos filho a clientes de automação, retornando os pares de automação de elementos que transmitem informações ou permitem a interação do usuário.  
  
<a name="Customizations"></a>
## <a name="customizations-in-a-derived-peer"></a>Personalizações em um par derivado  
 Todas as classes <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> que derivam <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>e contêm o método virtual protegido . O WPF chama <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> para obter o objeto de ponto de automação para cada controle. O código de automação pode usar o par para obter informações sobre recursos e características de um controle e para simular o uso interativo. Um controle personalizado que suporta <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> automação deve substituir e retornar uma <xref:System.Windows.Automation.Peers.AutomationPeer>instância de uma classe que deriva de . Por exemplo, se um controle <xref:System.Windows.Controls.Primitives.ButtonBase> personalizado deriva da classe, <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> então <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>o objeto retornado deve derivar de .  
  
 Ao implementar um controle personalizado, você deve substituir os métodos "Principais" da classe base par de automação que descrevem o comportamento exclusivo e específico ao seu controle personalizado.  
  
### <a name="override-oncreateautomationpeer"></a>Substituir OnCreateAutomationPeer  
 Anular o <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> método para o seu controle personalizado para que ele retorne o <xref:System.Windows.Automation.Peers.AutomationPeer>objeto do provedor, que deve derivar direta ou indiretamente de .  
  
### <a name="override-getpattern"></a>Substituir GetPattern  
 Os pares de automação simplificam alguns aspectos da implementação de provedores de [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] do lado do servidor, mas os pares de automação de controle personalizado ainda devem manipular as interfaces de padrões. Como provedores não-WPF, os pares suportam padrões <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> de controle <xref:System.Windows.Automation.Provider.IInvokeProvider>fornecendo implementações de interfaces no namespace, como . As interfaces de padrão de controle podem ser implementadas pelo próprio par ou por outro objeto. A implementação do <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> retorno do objeto que suporta o padrão especificado. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]código chama <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> o método <xref:System.Windows.Automation.Peers.PatternInterface> e especifica um valor de enumeração. Sua substituição <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> deve retornar o objeto que implementa o padrão especificado. Se o seu controle não tiver uma implementação personalizada de um <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> padrão, você pode chamar a implementação do tipo base de recuperar sua implementação ou nulo se o padrão não for suportado para este tipo de controle. Por exemplo, um controle NumericUpDown personalizado pode ser definido como [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] um valor <xref:System.Windows.Automation.Provider.IRangeValueProvider> dentro de um intervalo, para que seu par implemente a interface. O exemplo a seguir mostra <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> como o método do <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> peer é substituído para responder a um valor.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Um <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> método também pode especificar um subelemento como provedor de padrões. O código a <xref:System.Windows.Controls.ItemsControl> seguir mostra como as transferências <xref:System.Windows.Controls.ScrollViewer> de padrão de rolagem para o peer de seu controle interno.  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 Para especificar um subelemento para manipulação de padrões, esse código <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> obtém <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> o objeto subelemento, cria um peer usando o método, define a propriedade do novo peer para o par atual e retorna o novo peer. A <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> configuração de um subelemento impede que o subelemento apareça na árvore de pares de automação e <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>designa todos os eventos levantados pelo subelemento como originários do controle especificado em . O <xref:System.Windows.Controls.ScrollViewer> controle não aparece na árvore de automação, e eventos de <xref:System.Windows.Controls.ItemsControl> rolagem que ele gera parecem ter origem a partir do objeto.  
  
### <a name="override-core-methods"></a>Substituir métodos "Core"  
 O código de automação obtém informações sobre o controle chamando métodos públicos da classe par. Para fornecer informações sobre o controle, substitua cada método cujo nome termina com "Core" quando sua implementação de controle é diferente da que é fornecida pela classe base par de automação. No mínimo, seu controle <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> deve <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> implementar os métodos e métodos, como mostrado no exemplo a seguir.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Sua implementação <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> descreve seu controle <xref:System.Windows.Automation.ControlType> devolvendo um valor. Embora você <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>possa retornar, você deve retornar um dos tipos de controle mais específicos se ele descrever com precisão o seu controle. Um valor <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> de retorno de requer [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]trabalho [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] extra para o provedor implementar, e os produtos do cliente são incapazes de antecipar a estrutura de controle, a interação com o teclado e possíveis padrões de controle.  
  
 Implemente <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> os métodos e os métodos para indicar se o seu controle contém conteúdo de dados ou cumpre uma função interativa na interface do usuário (ou ambos). Por padrão, os dois os métodos retornam `true`. Essas configurações aprimoram a usabilidade de ferramentas de automação, como leitores de tela, que podem usar estes métodos para filtrar a árvore de automação. Se <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> o método transferir o manuseio de padrões para <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> um ponto de subelemento, o método do subelemento pode retornar falso para ocultar o ponto de subelemento da árvore de automação. Por exemplo, a <xref:System.Windows.Controls.ListBox> rolagem em <xref:System.Windows.Controls.ScrollViewer>a é manuseada por <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> um , <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> e o <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>ponto de automação para <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> é devolvido pelo método do que está associado ao . Portanto, o <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> método <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> dos `false`retornos, <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> para que o não apareça na árvore de automação.  
  
 Seu par de automação deve fornecer valores padrão apropriados para o seu controle. Observe que o XAML que faz referência ao seu controle pode <xref:System.Windows.Automation.AutomationProperties> substituir suas implementações de pares de métodos principais, incluindo atributos. Por exemplo, o XAML a seguir cria um botão que tem duas propriedades [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] personalizadas.  
  
```xaml  
<Button AutomationProperties.Name="Special"
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementar provedores de padrão  
 As interfaces implementadas por um provedor personalizado são explicitamente declaradas <xref:System.Windows.Controls.Control>se o elemento de propriedade derivar diretamente de . Por exemplo, o código a seguir <xref:System.Windows.Controls.Control> declara um peer para um que implementa um valor de intervalo.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Se o controle de possuir deriva de um <xref:System.Windows.Controls.Primitives.RangeBase>tipo específico de controle, como , o peer pode ser derivado de uma classe de pares derivada equivalente. Neste caso, o par <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>derivaria , que fornece <xref:System.Windows.Automation.Provider.IRangeValueProvider>uma implementação base de . O código a seguir mostra a declaração desse tipo de par.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Para uma implementação de exemplo, consulte o código fonte [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) ou [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) que implementa e consome um controle personalizado NumericUpDown.  
  
### <a name="raise-events"></a>Acionar eventos  
 Os clientes de automação podem assinar eventos de automação. Os controles personalizados devem relatar alterações no estado de controle, chamando o <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> método. Da mesma forma, quando um <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> valor de propriedade muda, chame o método. O código a seguir mostra como obter o objeto par de dentro do código do controle e como chamar um método para acionar um evento. Como uma otimização, o código determina se há algum ouvinte para esse tipo de evento. O acionamento do evento somente quando há ouvintes evita a sobrecarga desnecessária e ajuda o controle a permanecer responsivo.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral de automação da interface do usuário](../../ui-automation/ui-automation-overview.md)
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Controle personalizado NumericUpDown (C#) no GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Controle personalizado NumericUpDown (Visual Basic) no GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)

---
title: "Automação de interface do usuário de um controle personalizado do WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d10c11cfcacb435438695b0e76ee8982ba9ef24a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automação de interface do usuário de um controle personalizado do WPF
O [!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] fornece uma interface única e generalizada que os clientes de automação podem usar para examinar ou operar as interfaces do usuário de uma variedade de plataformas e estruturas. O [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] permite que o código de controle de qualidade (teste) e os aplicativos de acessibilidade, como leitores de tela, examinem os elementos de interface do usuário e simulem a interação do usuário com eles em outro código. Para obter informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] em todas as plataformas, consulte Acessibilidade.  
  
 Este tópico descreve como implementar um provedor da Automação da Interface do Usuário do lado do servidor para um controle personalizado que é executado em um aplicativo WPF. O WPF dá suporte ao [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] por meio de uma árvore de objetos pares de automação que se coloca em paralelo com a árvore de elementos de interface do usuário. O código de teste e os aplicativos que fornecem recursos de acessibilidade podem usar objetos pares de automação diretamente (para código em processo) ou por meio da interface generalizada fornecida pelo [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Classes par de automação  
 Suporte de controles WPF [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] por meio de uma árvore de classes de mesmo nível que derivam de <xref:System.Windows.Automation.Peers.AutomationPeer>. Por convenção, os nomes de classe pares começam com o nome de classe do controle e terminam com "AutomationPeer". Por exemplo, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> é a classe de ponto a ponto para o <xref:System.Windows.Controls.Button> classe de controle. As classes pares são mais ou menos equivalentes aos tipos de controle do [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], mas são específicas para elementos do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. O código de automação que acessa aplicativos WPF por meio da interface de [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] não usa pares de automação diretamente, mas o código de automação no mesmo espaço de processo pode usar pares de automação diretamente.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Classes pares de automação internas  
 Os elementos implementam uma classe par de automação se aceitam atividade proveniente da interface do usuário ou se contêm informações necessárias aos usuários de aplicativos de leitor de tela. Nem todos os elementos visuais do WPF têm pares de automação. Exemplos de classes que implementam os pares de automação são <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>, e <xref:System.Windows.Controls.Label>. Exemplos de classes que não implementam pares de automação são classes que derivam de <xref:System.Windows.Controls.Decorator>, como <xref:System.Windows.Controls.Border>e as classes com base em <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Controls.Canvas>.  
  
 A base de <xref:System.Windows.Controls.Control> classe não tem uma classe de par correspondente. Se você precisar de uma classe de ponto a ponto para corresponder a um controle personalizado que deriva de <xref:System.Windows.Controls.Control>, você deve derivar a classe de pares personalizado do <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Considerações de segurança para pares derivados  
 Os pares de automação devem ser executados em um ambiente de confiança parcial. O código no assembly UIAutomationClient não está configurado para ser executado em um ambiente de confiança parcial e o código par de automação não deve fazer referência a esse assembly. Em vez disso, você deve usar as classes no assembly UIAutomationTypes. Por exemplo, você deve usar o <xref:System.Windows.Automation.AutomationElementIdentifiers> classe do assembly UIAutomationTypes, que corresponde do <xref:System.Windows.Automation.AutomationElement> classe no assembly UIAutomationClient. É seguro fazer referência ao assembly UIAutomationTypes no código par de automação.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Navegação par  
 Depois de localizar um ponto de automação, o código no processo pode navegar na árvore de par chamando o objeto <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> e <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> métodos. Navegação entre [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementos dentro de um controle é suportado pela implementação do par do <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> método. O sistema de Automação da Interface do Usuário chama esse método para compilar uma árvore de subelementos contidos em um controle, por exemplo, itens de lista em uma caixa de listagem. O padrão <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> método percorre a árvore visual de elementos para criar a árvore de pares de automação. Os controles personalizados substituem esse método para expor elementos filho a clientes de automação, retornando os pares de automação de elementos que transmitem informações ou permitem a interação do usuário.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Personalizações em um par derivado  
 Todas as classes que derivam de <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement> contém o método virtual protegido <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. Chamadas WPF <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> para obter o objeto de mesmo nível de automação para cada controle. O código de automação pode usar o par para obter informações sobre recursos e características de um controle e para simular o uso interativo. Um controle personalizado que dá suporte à automação deve substituir <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> e retornar uma instância de uma classe que deriva de <xref:System.Windows.Automation.Peers.AutomationPeer>. Por exemplo, se um controle personalizado derivado de <xref:System.Windows.Controls.Primitives.ButtonBase> classe e, em seguida, o objeto retornado por <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> deve derivar de <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Ao implementar um controle personalizado, você deve substituir os métodos "Principais" da classe base par de automação que descrevem o comportamento exclusivo e específico ao seu controle personalizado.  
  
### <a name="override-oncreateautomationpeer"></a>Substituir OnCreateAutomationPeer  
 Substituir o <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> método para o controle personalizado para que retorne seu objeto de provedor, que deve derivar direta ou indiretamente de <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Substituir GetPattern  
 Os pares de automação simplificam alguns aspectos da implementação de provedores de [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] do lado do servidor, mas os pares de automação de controle personalizado ainda devem manipular as interfaces de padrões. Assim como provedores não-WPF, pontos oferecem suporte a padrões de controle, fornecendo implementações de interfaces no <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> namespace, como <xref:System.Windows.Automation.Provider.IInvokeProvider>. As interfaces de padrão de controle podem ser implementadas pelo próprio par ou por outro objeto. A implementação do par de <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> retorna o objeto que oferece suporte ao padrão especificado. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]código chama o <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> método e especifica um <xref:System.Windows.Automation.Peers.PatternInterface> valor de enumeração. A substituição de <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> deve retornar o objeto que implementa o padrão especificado. Se o controle não tem uma implementação personalizada de um padrão, você pode chamar a implementação do tipo base do <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> para recuperar sua implementação ou o null se não há suporte para o padrão para esse tipo de controle. Por exemplo, um controle NumericUpDown personalizado pode ser definido como um valor em um intervalo, para que seu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] par implementaria o <xref:System.Windows.Automation.Provider.IRangeValueProvider> interface. A exemplo a seguir mostra como o par <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> método é substituído para responder a um <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> valor.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Um <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> método também pode especificar um subelemento como um provedor padrão. O código a seguir mostra como <xref:System.Windows.Controls.ItemsControl> transferências rolagem tratamento padrão para o par de interna <xref:System.Windows.Controls.ScrollViewer> controle.  
  
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
  
 Para especificar um subelemento para manipulação do padrão, esse código obtém o objeto de subelemento, cria uma ponto a ponto usando o <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> método, define o <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> propriedade do novo ponto para o ponto atual e retorna a novo ponto a ponto. Configuração <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> em um subelemento impede que o subelemento que aparecem na árvore de mesmo nível de automação e designa todos os eventos gerados pelo subelemento como originado do controle especificado em <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. O <xref:System.Windows.Controls.ScrollViewer> controle não aparecem na árvore de automação e eventos de rolagem que ele gera aparecem originar o <xref:System.Windows.Controls.ItemsControl> objeto.  
  
### <a name="override-core-methods"></a>Substituir métodos "Core"  
 O código de automação obtém informações sobre o controle chamando métodos públicos da classe par. Para fornecer informações sobre o controle, substitua cada método cujo nome termina com "Core" quando sua implementação de controle é diferente da que é fornecida pela classe base par de automação. No mínimo, o controle deve implementar o <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> e <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> métodos, como mostrado no exemplo a seguir.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 A implementação do <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> descreve seu controle retornando um <xref:System.Windows.Automation.ControlType> valor. Embora você possa retornar <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, você deve retornar um dos tipos de controle mais específicos se ele descreve com precisão o controle. Um valor de retorno <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> requer trabalho adicional para o provedor a implementar [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], e [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] produtos de cliente não for possível prever a estrutura de controle, interação de teclado e padrões de controle possíveis.  
  
 Implementar o <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> e <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> métodos para indicar se o controle de dados de conteúdo ou atende a uma função interativa na interface do usuário (ou ambos). Por padrão, os dois os métodos retornam `true`. Essas configurações aprimoram a usabilidade de ferramentas de automação, como leitores de tela, que podem usar estes métodos para filtrar a árvore de automação. Se seu <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> método transferências padrão para um par de subelemento, o par de subelemento <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> método pode retornar false para ocultar o par de subelemento da árvore de automação. Rolagem por exemplo, em um <xref:System.Windows.Controls.ListBox> é tratado por um <xref:System.Windows.Controls.ScrollViewer>e o par de automação para <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> é retornado pelo <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> método do <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> que está associado a <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Portanto, o <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> método o <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> retorna `false`, de modo que o <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> não aparecem na árvore de automação.  
  
 Seu par de automação deve fornecer valores padrão apropriados para o seu controle. Observe que o XAML que faz referência a seu controle pode substituir suas implementações de par de métodos de núcleo, incluindo <xref:System.Windows.Automation.AutomationProperties> atributos. Por exemplo, o XAML a seguir cria um botão que tem duas propriedades [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] personalizadas.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementar provedores de padrão  
 As interfaces implementadas por um provedor personalizado são explicitamente declaradas se o elemento dono deriva diretamente da <xref:System.Windows.Controls.Control>. Por exemplo, o código a seguir declara um par para um <xref:System.Windows.Controls.Control> que implementa um valor de intervalo.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Se o controle dono deriva de um tipo específico de controle, como <xref:System.Windows.Controls.Primitives.RangeBase>, a ponto a ponto pode ser derivada de uma classe peer derivada equivalente. Nesse caso, o par deve derivar de <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, que fornece uma implementação de base de <xref:System.Windows.Automation.Provider.IRangeValueProvider>. O código a seguir mostra a declaração desse tipo de par.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 Para uma implementação de exemplo, consulte [Exemplo de controle personalizado NumericUpDown com tema e suporte de Automação da Interface do Usuário](http://go.microsoft.com/fwlink/?LinkID=160025).  
  
### <a name="raise-events"></a>Acionar eventos  
 Os clientes de automação podem assinar eventos de automação. Controles personalizados devem reportar alterações para controlar o estado chamando o <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> método. Da mesma forma, quando um valor de propriedade alterado, chame o <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> método. O código a seguir mostra como obter o objeto par de dentro do código do controle e como chamar um método para acionar um evento. Como uma otimização, o código determina se há algum ouvinte para esse tipo de evento. O acionamento do evento somente quando há ouvintes evita a sobrecarga desnecessária e ajuda o controle a permanecer responsivo.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de automação de interface do usuário](../../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [Controle NumericUpDown personalizado com tema e exemplo de suporte de automação de interface do usuário](http://go.microsoft.com/fwlink/?LinkID=160025)  
 [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)

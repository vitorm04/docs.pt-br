---
title: Automação de interface do usuário de um controle personalizado do WPF
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
ms.openlocfilehash: 1cafb6cf8fd5096e2c17d2687ec390db06faf873
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636062"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automação de interface do usuário de um controle personalizado do WPF
O [!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] fornece uma interface única e generalizada que os clientes de automação podem usar para examinar ou operar as interfaces do usuário de uma variedade de plataformas e estruturas. O [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] permite que o código de controle de qualidade (teste) e os aplicativos de acessibilidade, como leitores de tela, examinem os elementos de interface do usuário e simulem a interação do usuário com eles em outro código. Para obter informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] em todas as plataformas, consulte Acessibilidade.  
  
 Este tópico descreve como implementar um provedor da Automação da Interface do Usuário do lado do servidor para um controle personalizado que é executado em um aplicativo WPF. O WPF dá suporte ao [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] por meio de uma árvore de objetos pares de automação que se coloca em paralelo com a árvore de elementos de interface do usuário. O código de teste e os aplicativos que fornecem recursos de acessibilidade podem usar objetos pares de automação diretamente (para código em processo) ou por meio da interface generalizada fornecida pelo [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Classes par de automação  
 Os controles WPF dão suporte a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] por meio de uma árvore de classes pares que derivam de <xref:System.Windows.Automation.Peers.AutomationPeer>. Por convenção, os nomes de classe pares começam com o nome de classe do controle e terminam com "AutomationPeer". Por exemplo, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> é a classe par para a classe de controle de <xref:System.Windows.Controls.Button>. As classes pares são aproximadamente equivalentes a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] tipos de controle, mas são específicas para elementos do WPF. O código de automação que acessa aplicativos WPF por meio da interface de [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] não usa pares de automação diretamente, mas o código de automação no mesmo espaço de processo pode usar pares de automação diretamente.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Classes pares de automação internas  
 Os elementos implementam uma classe par de automação se aceitam atividade proveniente da interface do usuário ou se contêm informações necessárias aos usuários de aplicativos de leitor de tela. Nem todos os elementos visuais do WPF têm pares de automação. Os exemplos de classes que implementam os pares de automação são <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>e <xref:System.Windows.Controls.Label>. Exemplos de classes que não implementam os pares de automação são classes que derivam de <xref:System.Windows.Controls.Decorator>, como <xref:System.Windows.Controls.Border>e classes baseadas em <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Grid> e <xref:System.Windows.Controls.Canvas>.  
  
 A classe de <xref:System.Windows.Controls.Control> base não tem uma classe par correspondente. Se você precisar de uma classe par para corresponder a um controle personalizado que deriva de <xref:System.Windows.Controls.Control>, deverá derivar a classe de par personalizada de <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Considerações de segurança para pares derivados  
 Os pares de automação devem ser executados em um ambiente de confiança parcial. O código no assembly UIAutomationClient não está configurado para ser executado em um ambiente de confiança parcial e o código par de automação não deve fazer referência a esse assembly. Em vez disso, você deve usar as classes no assembly UIAutomationTypes. Por exemplo, você deve usar a classe <xref:System.Windows.Automation.AutomationElementIdentifiers> do assembly UIAutomationTypes, que corresponde à classe <xref:System.Windows.Automation.AutomationElement> no assembly UIAutomationClient. É seguro fazer referência ao assembly UIAutomationTypes no código par de automação.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Navegação par  
 Depois de localizar um par de automação, o código em processo pode navegar pela árvore de pares chamando os métodos de <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> e <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> do objeto. Há suporte para a navegação entre elementos do WPF dentro de um controle pela implementação do par do método <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A>. O sistema de Automação da Interface do Usuário chama esse método para compilar uma árvore de subelementos contidos em um controle, por exemplo, itens de lista em uma caixa de listagem. O método <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> padrão percorre a árvore visual de elementos para criar a árvore de pares de automação. Os controles personalizados substituem esse método para expor elementos filho a clientes de automação, retornando os pares de automação de elementos que transmitem informações ou permitem a interação do usuário.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Personalizações em um par derivado  
 Todas as classes que derivam de <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement> contêm o método virtual protegido <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. O WPF chama <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> para obter o objeto par de automação para cada controle. O código de automação pode usar o par para obter informações sobre recursos e características de um controle e para simular o uso interativo. Um controle personalizado que dá suporte à automação deve substituir <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> e retornar uma instância de uma classe derivada de <xref:System.Windows.Automation.Peers.AutomationPeer>. Por exemplo, se um controle personalizado deriva da classe <xref:System.Windows.Controls.Primitives.ButtonBase>, o objeto retornado por <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> deve derivar de <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Ao implementar um controle personalizado, você deve substituir os métodos "Principais" da classe base par de automação que descrevem o comportamento exclusivo e específico ao seu controle personalizado.  
  
### <a name="override-oncreateautomationpeer"></a>Substituir OnCreateAutomationPeer  
 Substitua o método <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> para seu controle personalizado para que ele retorne o objeto de provedor, que deve derivar direta ou indiretamente do <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Substituir GetPattern  
 Os pares de automação simplificam alguns aspectos da implementação de provedores de [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] do lado do servidor, mas os pares de automação de controle personalizado ainda devem manipular as interfaces de padrões. Assim como os provedores não-WPF, os pares dão suporte a padrões de controle fornecendo implementações de interfaces no namespace <xref:System.Windows.Automation.Provider?displayProperty=nameWithType>, como <xref:System.Windows.Automation.Provider.IInvokeProvider>. As interfaces de padrão de controle podem ser implementadas pelo próprio par ou por outro objeto. A implementação do par de <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> retorna o objeto que dá suporte ao padrão especificado. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] código chama o método <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> e especifica um valor de enumeração <xref:System.Windows.Automation.Peers.PatternInterface>. A substituição de <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> deve retornar o objeto que implementa o padrão especificado. Se o seu controle não tiver uma implementação personalizada de um padrão, você poderá chamar a implementação do tipo base de <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> para recuperar sua implementação ou NULL se o padrão não tiver suporte para esse tipo de controle. Por exemplo, um controle NumericUpDown personalizado pode ser definido como um valor dentro de um intervalo, de modo que seu [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] de mesmo nível implementaria a interface <xref:System.Windows.Automation.Provider.IRangeValueProvider>. O exemplo a seguir mostra como o método de <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> do par é substituído para responder a um valor de <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType>.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Um método <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> também pode especificar um subelemento como um provedor de padrão. O código a seguir mostra como <xref:System.Windows.Controls.ItemsControl> transfere o tratamento do padrão de rolagem para o par de seu controle de <xref:System.Windows.Controls.ScrollViewer> interno.  
  
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
  
 Para especificar um subelemento para tratamento de padrões, esse código obtém o objeto de subelemento, cria um par usando o método <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>, define a propriedade <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> do novo ponto para o par atual e retorna o novo par. A configuração <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> em um subelemento impede que o subelemento apareça na árvore de mesmo nível de automação e designa todos os eventos gerados pelo subelemento como provenientes do controle especificado em <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. O controle de <xref:System.Windows.Controls.ScrollViewer> não aparece na árvore de automação e a rolagem de eventos que ele gera parece ser originada do objeto <xref:System.Windows.Controls.ItemsControl>.  
  
### <a name="override-core-methods"></a>Substituir métodos "Core"  
 O código de automação obtém informações sobre o controle chamando métodos públicos da classe par. Para fornecer informações sobre o controle, substitua cada método cujo nome termina com "Core" quando sua implementação de controle é diferente da que é fornecida pela classe base par de automação. No mínimo, o controle deve implementar os métodos <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> e <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Sua implementação de <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> descreve seu controle retornando um valor de <xref:System.Windows.Automation.ControlType>. Embora seja possível retornar <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, você deve retornar um dos tipos de controle mais específicos se ele descrever com precisão seu controle. Um valor de retorno de <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> requer trabalho extra para o provedor implementar [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], e [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] produtos cliente não podem prever a estrutura de controle, a interação do teclado e os padrões de controle possíveis.  
  
 Implemente os métodos <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> e <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> para indicar se o seu controle contém conteúdo de dados ou atende a uma função interativa na interface do usuário (ou ambos). Por padrão, os dois os métodos retornam `true`. Essas configurações aprimoram a usabilidade de ferramentas de automação, como leitores de tela, que podem usar estes métodos para filtrar a árvore de automação. Se o método <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> transfere o tratamento de padrões para um par de subelemento, o método <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> do par de subelemento pode retornar false para ocultar o par subelemento da árvore de automação. Por exemplo, a rolagem em uma <xref:System.Windows.Controls.ListBox> é manipulada por um <xref:System.Windows.Controls.ScrollViewer>, e o ponto de automação para <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> é retornado pelo método <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> da <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> associada ao <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Portanto, o método <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> da <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> retorna `false`, para que o <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> não apareça na árvore de automação.  
  
 Seu par de automação deve fornecer valores padrão apropriados para o seu controle. Observe que o XAML que faz referência ao seu controle pode substituir as implementações de mesmo nível dos métodos principais, incluindo atributos de <xref:System.Windows.Automation.AutomationProperties>. Por exemplo, o XAML a seguir cria um botão que tem duas propriedades [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] personalizadas.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementar provedores de padrão  
 As interfaces implementadas por um provedor personalizado são declaradas explicitamente se o elemento proprietário deriva diretamente de <xref:System.Windows.Controls.Control>. Por exemplo, o código a seguir declara um par para um <xref:System.Windows.Controls.Control> que implementa um valor de intervalo.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Se o controle proprietário derivar de um tipo específico de controle, como <xref:System.Windows.Controls.Primitives.RangeBase>, o par poderá ser derivado de uma classe par derivada equivalente. Nesse caso, o par derivaria de <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, que fornece uma implementação base de <xref:System.Windows.Automation.Provider.IRangeValueProvider>. O código a seguir mostra a declaração desse tipo de par.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Para obter um exemplo de implementação, [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) consulte o código-fonte do ou [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) que implementa e consome um controle personalizado NumericUpDown.  
  
### <a name="raise-events"></a>Acionar eventos  
 Os clientes de automação podem assinar eventos de automação. Os controles personalizados devem relatar alterações no estado de controle chamando o método <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>. Da mesma forma, quando um valor de propriedade é alterado, chame o método <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>. O código a seguir mostra como obter o objeto par de dentro do código do controle e como chamar um método para acionar um evento. Como uma otimização, o código determina se há algum ouvinte para esse tipo de evento. O acionamento do evento somente quando há ouvintes evita a sobrecarga desnecessária e ajuda o controle a permanecer responsivo.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Veja também

- [Visão geral de Automação da Interface do Usuário](../../ui-automation/ui-automation-overview.md)
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Controle personalizado NumericUpDown (C#) no github](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Controle personalizado NumericUpDown (Visual Basic) no GitHub](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)

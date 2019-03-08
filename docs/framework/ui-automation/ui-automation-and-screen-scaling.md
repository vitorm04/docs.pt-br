---
title: Automação da Interface do Usuário e Escala da Tela
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: 4b2988314afbe501623fd050a989876842f68601
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674530"
---
# <a name="ui-automation-and-screen-scaling"></a>Automação da Interface do Usuário e Escala da Tela
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] permite que os usuários alterem a [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] definindo assim que a maior parte [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos na tela pareçam maiores. Embora esse recurso tenha sido disponibilizado no [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], nas versões anteriores a escala precisava ser implementada pelos aplicativos. No [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], o Gerenciador de janelas da área de trabalho executa a escala padrão para todos os aplicativos que não lidam com seus próprios recursos de dimensionamento. Aplicativos cliente de automação de interface do usuário devem levar esse recurso em conta.  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Dimensionamento no Windows Vista  
 O padrão [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] configuração é 96, o que significa que 96 pixels ocupam uma largura ou altura de uma polegada teórica. A medida exata de uma polegada"" depende do tamanho e resolução física do monitor. Por exemplo, em um monitor de 12 polegadas de largura, em uma resolução horizontal de 1280 pixels, uma linha horizontal de 96 pixels estende cerca de 9/10 de uma polegada.  
  
 Alterando o [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] configuração não é o mesmo que alterar a resolução da tela. Com [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] dimensionamento, o número de pixels físicos na tela permanece o mesmo. No entanto, a escala é aplicada ao tamanho e local do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos. Esse dimensionamento pode ser executada automaticamente pelo Desktop Window Manager (DWM) para a área de trabalho e para aplicativos que não pedir explicitamente para não ser dimensionado.  
  
 Na verdade, quando o usuário define o fator de escala para 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], uma polegada vertical ou horizontal na tela se torna maior em 25 por cento. Todas as dimensões são dimensionadas de acordo. O deslocamento da janela do aplicativo, as bordas superior e esquerda da tela aumenta em 25 por cento. Se o dimensionamento do aplicativo estiver habilitado e o aplicativo não está [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-ciente, o tamanho da janela aumenta na mesma proporção, juntamente com os deslocamentos e tamanhos de todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos que ele contém.  
  
> [!NOTE]
>  Por padrão, o DWM não executa o redimensionamento de não -[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-aplicativos com reconhecimento de quando o usuário define o [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] como 120, mas o faz quando o [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] é definido como um valor personalizado de 144 ou superior. No entanto, o usuário pode substituir o comportamento padrão.  
  
 Escala da tela cria novos desafios para aplicativos com a preocupação de qualquer maneira com coordenadas de tela. A tela agora contém dois sistemas de coordenadas: física e lógica. As coordenadas físicas de um ponto são o deslocamento real em pixels do canto superior esquerdo da origem. As coordenadas lógicas são os deslocamentos como seriam se os próprios pixels foram escalados.  
  
 Suponha que você crie uma caixa de diálogo com um botão nas coordenadas (100, 48). Quando essa caixa de diálogo é exibida no padrão 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], o botão está localizado nas coordenadas físicas (100, 48). Em 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)], ele está localizado nas coordenadas físicas (125, 60). Mas as coordenadas lógicas são as mesmas em qualquer [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] configuração: (100, 48).  
  
 Coordenadas lógicas são importantes, pois elas simplificam o comportamento do sistema operacional e dos aplicativos consistente, independentemente do [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] configuração. Por exemplo, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normalmente retorna as coordenadas lógicas. Se você mover o cursor sobre um elemento em uma caixa de diálogo, as mesmas coordenadas são retornadas, independentemente do [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] configuração. Se você desenhar um controle em (100, 100), ele é desenhado nessas coordenadas lógicas e ocupará a mesma posição relativa em qualquer [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] configuração.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>Dimensionamento em clientes de automação de interface do usuário  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] não usa coordenadas lógicas. Os métodos e propriedades a seguir retornam coordenadas físicas ou levá-los como parâmetros.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Por padrão, um aplicativo de cliente de automação de interface do usuário em execução em um não-96 - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] ambiente não poderá obter resultados corretos esses métodos e propriedades. Por exemplo, como a posição do cursor está em coordenadas lógicas, o cliente não pode simplesmente passar essas coordenadas para <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> para obter o elemento que está sob o cursor. Além disso, o aplicativo não poderá posicionar corretamente janelas fora de sua área de cliente.  
  
 A solução é em duas partes.  
  
1.  Primeiro, verifique o aplicativo cliente [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-ciente. Para fazer isso, chame o [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] função `SetProcessDPIAware` na inicialização. No código gerenciado, a seguinte declaração disponibiliza essa função.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Essa função faz com que todo o processo de reconhecimento de dpi, que significa que todas as janelas que pertencem ao processo são fora de escala. No [exemplo de marca-texto](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), por exemplo, as quatro janelas que compõem o retângulo de realce estão localizadas nas coordenadas físicas obtidas de automação de interface do usuário, não nas coordenadas lógicas. Se o exemplo não estava cientes de dpi, o realce poderia ser desenhado nas coordenadas lógicas na área de trabalho, o que resulta na colocação incorreta em um ambiente de não-96-dpi.  
  
2.  Para obter as coordenadas do cursor, chame o [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] função `GetPhysicalCursorPos`. O exemplo a seguir mostra como declarar e usar essa função.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  Não use <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. O comportamento dessa propriedade fora das janelas de cliente em um ambiente em escala é indefinido.  
  
 Se seu aplicativo realiza a comunicação direta entre processos com não - [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]-com suporte a aplicativos, talvez seja necessário converter entre coordenadas lógicas e físicas usando o [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] funções `PhysicalToLogicalPoint` e `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>Consulte também
- [Exemplo de marca-texto](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)

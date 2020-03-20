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
ms.openlocfilehash: 2a68a74fa6aadcaba21f142d394a1f8a3d8af371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179977"
---
# <a name="ui-automation-and-screen-scaling"></a>Automação da Interface do Usuário e Escala da Tela
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
Começando pelo Windows Vista, o Windows permite que os usuários alterem a configuração de pontos por polegada (dpi) para que a maioria dos elementos de interface do usuário (UI) na tela pareça maior. Embora esse recurso esteja disponível há muito tempo no Windows, em versões anteriores o dimensionamento tinha que ser implementado por aplicativos. Começando pelo Windows Vista, o Desktop Window Manager executa o dimensionamento padrão para todos os aplicativos que não lidam com seu próprio dimensionamento. Os aplicativos clientes de automação de interface do usuário devem levar esse recurso em conta.  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a>Dimensionamento no Windows Vista  
 A configuração padrão do dpi é 96, o que significa que 96 pixels ocupam uma largura ou altura de uma polegada nocional. A medida exata de uma "polegada" depende do tamanho e resolução física do monitor. Por exemplo, em um monitor de 12 polegadas de largura, com uma resolução horizontal de 1280 pixels, uma linha horizontal de 96 pixels se estende por cerca de 9/10 de polegada.  
  
 Alterar a configuração de dpi não é o mesmo que alterar a resolução da tela. Com o dimensionamento de dpi, o número de pixels físicos na tela permanece o mesmo. No entanto, o dimensionamento é [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplicado ao tamanho e localização dos elementos. Esse dimensionamento pode ser realizado automaticamente pelo Desktop Window Manager (DWM) para a área de trabalho e para aplicativos que não pedem explicitamente para não serem dimensionados.  
  
 Com efeito, quando o usuário define o fator de escala para 120 dpi, uma polegada vertical ou horizontal na tela torna-se maior em 25%. Todas as dimensões são dimensionadas em conformidade. O deslocamento de uma janela de aplicação das bordas superior e esquerda da tela aumenta em 25%. Se o dimensionamento do aplicativo estiver ativado e o aplicativo não estiver consciente do dpi, o tamanho [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] da janela aumentará na mesma proporção, juntamente com as compensações e tamanhos de todos os elementos que ele contém.  
  
> [!NOTE]
> Por padrão, o DWM não executa o dimensionamento para aplicativos não-dpi-aware quando o usuário define o dpi para 120, mas executa-o quando o dpi é definido como um valor personalizado de 144 ou mais. No entanto, o usuário pode substituir o comportamento padrão.  
  
 O dimensionamento da tela cria novos desafios para aplicativos que estão preocupados de alguma forma com as coordenadas da tela. A tela agora contém dois sistemas de coordenadas: físico e lógico. As coordenadas físicas de um ponto são o deslocamento real em pixels do canto superior esquerdo da origem. As coordenadas lógicas são os deslocamentos como seriam se os pixels fossem escalados.  
  
 Suponha que você projete uma caixa de diálogo com um botão nas coordenadas (100, 48). Quando esta caixa de diálogo é exibida no padrão de 96 dpi, o botão está localizado nas coordenadas físicas de (100, 48). Com 120 dpi, está localizado em coordenadas físicas de (125, 60). Mas as coordenadas lógicas são as mesmas em qualquer configuração de dpi: (100, 48).  
  
 Coordenadas lógicas são importantes, pois tornam o comportamento do sistema operacional e das aplicações consistente, independentemente da configuração do DPI. Por exemplo, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normalmente retorna as coordenadas lógicas. Se você mover o cursor sobre um elemento em uma caixa de diálogo, as mesmas coordenadas serão devolvidas independentemente da configuração de dpi. Se você desenhar um controle em (100, 100), ele é atraído para essas coordenadas lógicas, e ocupará a mesma posição relativa em qualquer configuração de dpi.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a>Dimensionamento em clientes de automação de interface do usuário  
 A [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API não usa coordenadas lógicas. Os seguintes métodos e propriedades retornam coordenadas físicas ou tomam como parâmetros.  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 Por padrão, um aplicativo cliente de automação de interface do usuário em execução em um ambiente não-96-dpi não será capaz de obter resultados corretos desses métodos e propriedades. Por exemplo, como a posição do cursor está em coordenadas <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> lógicas, o cliente não pode simplesmente passar essas coordenadas para obter o elemento que está sob o cursor. Além disso, o aplicativo não será capaz de colocar corretamente janelas fora de sua área cliente.  
  
 A solução está em duas partes.  
  
1. Primeiro, faça com que o aplicativo cliente seja informado. Para isso, ligue para a `SetProcessDPIAware` função Win32 na inicialização. No código gerenciado, a seguinte declaração disponibiliza essa função.  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     Essa função torna todo o processo consciente, o que significa que todas as janelas que pertencem ao processo não são dimensionadas. Na [Amostra de Marcador,](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)por exemplo, as quatro janelas que compõem o retângulo de destaque estão localizadas nas coordenadas físicas obtidas da UI Automation, não nas coordenadas lógicas. Se a amostra não estivesse ciente do dpi, o destaque seria desenhado nas coordenadas lógicas da área de trabalho, o que resultaria em colocação incorreta em um ambiente não-96-dpi.  
  
2. Para obter as coordenadas do cursor, ligue para a função `GetPhysicalCursorPos`Win32 . O exemplo a seguir mostra como declarar e usar esta função.  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> Não use <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>. O comportamento desta propriedade fora das janelas do cliente em um ambiente escalonado é indefinido.  
  
 Se o aplicativo realizar comunicação direta entre processos com aplicativos não-conscientes de dpi, você pode ter `PhysicalToLogicalPoint` convertido `LogicalToPhysicalPoint`entre coordenadas lógicas e físicas usando as funções Win32 e .  
  
## <a name="see-also"></a>Confira também

- [Amostra do marcador](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)

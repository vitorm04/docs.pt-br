---
title: Práticas recomendadas de Acessibilidade
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: c6f0f31260ffae43e59703ef53dd7ef30a73320b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180292"
---
# <a name="accessibility-best-practices"></a>Práticas recomendadas de Acessibilidade
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 A implementação das seguintes práticas recomendadas em controles ou aplicativos melhorará sua acessibilidade para pessoas que usam dispositivos de tecnologia assistiva. Muitas dessas melhores práticas se [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] concentram em um bom design. Cada prática recomendada inclui [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] informações de implementação para controles ou aplicativos. Em muitos casos, o trabalho para atender a [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] essas melhores práticas já está incluído nos controles.  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a>Acesso Programático  
 O acesso programático envolve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] garantir que todos os elementos sejam rotulados, que os valores da propriedade sejam expostos e os eventos apropriados sejam levantados. Para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controles padrão, a maior parte <xref:System.Windows.Automation.Peers.AutomationPeer>deste trabalho já é feito através de . Controles personalizados exigem trabalho adicional para garantir que o acesso programático seja implementado corretamente.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Habilite o acesso programático a todos os elementos e textos de ui  
 Os elementos de interface do usuário (UI) devem permitir o acesso programático. Se [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] for um [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controle padrão, o suporte ao acesso programático está incluído no controle. Se o controle é um controle personalizado – um controle que foi subclassificado a partir de um controle <xref:System.Windows.Automation.Peers.AutomationPeer> comum ou um controle que foi subclassificado do Controle – então você deve verificar a implementação para áreas que podem precisar de modificação.  
  
 Seguindo essa prática recomendada, os fornecedores de tecnologia assistiva identificam e manipulam elementos do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]seu produto.  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Coloque nomes, títulos e descrições em objetos, quadros e páginas de ida e respostas  
 As tecnologias assistivas, especialmente os leitores de tela, usam o título para entender a localização do quadro, objeto ou página no esquema de navegação. Portanto, o título deve ser muito descritivo. Por exemplo, um título de página da Web de "Microsoft Web Page" é inútil se o usuário navegou profundamente em alguma área específica. Um título descritivo é fundamental para usuários cegos e dependem de leitores de tela. Da mesma [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] forma, <xref:System.Windows.Automation.AutomationProperties.NameProperty> para <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> controles, e são importantes para dispositivos de tecnologia assistiva.  
  
 Seguindo essa prática recomendada permite que as [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tecnologias assistivas identifiquem e manipulem em controles e aplicações de amostras.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Garantir que eventos programáticos sejam acionados por todas as atividades da UI  
 Seguindo essa prática recomendada permite que as tecnologias [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] assistivas ouçam as mudanças no e notifiquem o usuário sobre essas alterações.  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a>Configurações do usuário  
 A melhor prática nesta seção garante que os controles ou aplicativos não sobreponham as configurações do usuário.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Respeite todas as configurações de todo o sistema e não interfira nas funções de acessibilidade  
 Os usuários podem usar o Painel de Controle para definir algumas bandeiras em todo o sistema; outras bandeiras podem ser definidas programáticamente. Essas configurações não devem ser alteradas por controles ou aplicativos. Além disso, os aplicativos devem suportar as configurações de acessibilidade do sistema operacional host.  
  
 Seguindo essa prática recomendada, os usuários definem configurações de acessibilidade e sabem que essas configurações não serão alteradas por aplicativos.  
  
<a name="Visual_UI_Design"></a>
## <a name="visual-ui-design"></a>Visual UI Design  
 As práticas recomendadas nesta seção garantem que os controles ou aplicativos usem cores e imagens de forma eficaz e possam ser usados por tecnologias assistivas.  
  
<a name="Don_t_Hard_Code_Colors"></a>
### <a name="dont-hard-code-colors"></a>Não Embutir Cores  
 Pessoas que são cegas por cores, têm baixa visão ou estão usando uma tela em preto e branco podem não ser capazes de usar aplicativos com cores codificadas.  
  
 Seguindo essa prática recomendada, os usuários ajustam combinações de cores com base nas necessidades individuais.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Suporte alto contraste e todos os atributos de exibição do sistema  
 Os aplicativos não devem interromper ou desativar configurações de contraste selecionadas pelo usuário, configurações de contraste em todo o sistema, seleções de cores ou outras configurações e atributos de exibição em todo o sistema. As configurações em todo o sistema adotadas por um usuário aumentam a acessibilidade dos aplicativos, de modo que eles não devem ser desativados ou desconsiderados pelos aplicativos. A cor deve ser usada na combinação de primeiro plano de fundo correta para fornecer contraste adequado. As cores não relacionadas não devem ser misturadas, e as cores não devem ser invertidas.  
  
 Muitos usuários exigem combinações específicas de alto contraste, como texto branco em um fundo preto. Desenhar estes invertidos, como texto preto em um fundo branco faz com que o fundo sangre sobre o primeiro plano e pode dificultar a leitura para alguns usuários.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Certifique-se de que todas as escalas de iue corretamente por qualquer configuração de DPI  
 Certifique-se [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de que todos podem dimensionar corretamente por qualquer configuração de ponto por polegada (dpi). Além disso, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] certifique-se de que os elementos se encaixam em uma tela de 1024 x 768 com 120 pontopor polegada (dpi).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Navegação  
 As práticas recomendadas nesta seção garantem que a navegação tenha sido endereçada para controles e aplicativos.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Fornecer interface de teclado para todos os elementos de interface de interface  
 As paradas de guia, especialmente quando cuidadosamente planejadas, dão aos usuários outra maneira de navegar. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]  
  
 Os aplicativos devem fornecer as seguintes interfaces de teclado:  
  
- guia pára para todos os controles com os quais o usuário pode interagir, como botões, links ou caixas de lista  
  
- ordem de guia lógica  
  
<a name="Show_the_Keyboard_Focus"></a>
### <a name="show-the-keyboard-focus"></a>Mostrar o foco do teclado  
 Os usuários precisam saber qual objeto tem o foco do teclado para que eles possam antecipar o efeito de suas teclas. Para destacar o foco do teclado, use cores, fontes ou gráficos, como retângulos ou ampliação. Para destacar audivelmente o foco do teclado, altere o volume, o tom ou a qualidade tonal.  
  
 Para evitar confusão, os aplicativos devem ocultar todos os indicadores de foco visual e dim selections que estão localizados em janelas inativas (ou painéis).  
  
 Os aplicativos devem fazer o seguinte com foco no teclado:  
  
- um item deve sempre ter foco no teclado  
  
- foco do teclado deve ser visível e óbvio  
  
- seleções e/ou itens focados devem ser destacados visualmente  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Padrões de navegação de suporte e poderosos esquemas de navegação  
 Diferentes aspectos da navegação do teclado fornecem [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]diferentes maneiras para os usuários navegarem pelo .  
  
 Os aplicativos devem fornecer as seguintes interfaces de teclado:  
  
- chaves de atalho e teclas de acesso sublinhadas para todos os comandos, menus e controles  
  
- atalhos de teclado para links importantes  
  
- todos os itens do menu têm uma chave de acesso; todos os botões têm teclas do acelerador, todos os comandos têm uma chave do acelerador.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Não deixe que a localização do mouse interfira na navegação do teclado  
 A localização do mouse não deve interferir na navegação do teclado. Por exemplo, se o mouse estiver posicionado em algum lugar e o usuário estiver navegando com o teclado, um clique do mouse não deve acontecer a menos que seja iniciado pelo usuário.  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a>Multimodal Interface  
 As práticas recomendadas nesta [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] seção garantem que a aplicação inclua alternativas para elementos visuais.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Forneça equivalentes selecionáveis pelo usuário para elementos não-texto  
 Para cada elemento que não seja texto, forneça um equivalente selecionável pelo usuário para texto, transcrições ou descrições de áudio, como texto alt, legendas ou feedback visual.  
  
 Elementos não-texmrais [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] abrangem uma ampla gama de elementos, incluindo: imagens, regiões do mapa de imagem, animações, applets, quadros, scripts, botões gráficos, sons, arquivos de áudio e vídeo autônomos. Elementos não-texto são importantes quando contêm informações visuais, fala ou informações de áudio gerais [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]às quais o usuário precisa acessar para entender o conteúdo do .  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Use cor, mas também forneça alternativas à cor  
 Use a cor para melhorar, enfatizar ou reiterar informações mostradas por outros meios, mas não comunique informações usando apenas cores. Usuários que são cegos de cor ou têm um display monocromático precisam de alternativas para colorir.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Use APIs de entrada padrão com chamadas independentes de dispositivo  
 Chamadas independentes de dispositivos garantem a igualdade entre os recursos de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]teclado e mouse, ao mesmo tempo em que fornecem tecnologia assistiva com informações necessárias sobre o .  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.Peers>
- [Exemplo de controle personalizado NumericUpDown com tema e suporte de Automação da Interface do Usuário](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Diretrizes para design de interface do usuário do teclado](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)

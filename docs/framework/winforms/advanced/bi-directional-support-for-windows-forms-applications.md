---
title: Suporte bidirecional para aplicativos do Windows Forms
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2811674ad8d870062e3a0c67dbd21e6550f6c48d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655672"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Suporte bidirecional para aplicativos do Windows Forms
Você pode usar o Visual Studio para criar aplicativos baseados no Windows que dão suporte a espelhamento bidirecional (direita para esquerda) idiomas como árabe e hebraico. Isso inclui formulários padrão, caixas de diálogo, formulários MDI e todos os controles que você pode trabalhar com esses formulários — ou seja, todos os objetos no <xref:System.Windows.Forms.Control> namespace.  
  
## <a name="culture-support"></a>Suporte a cultura  
 Configurações de cultura e da interface do usuário determinam como um aplicativo funciona com datas, horas, moeda e outras informações. Suporte para a cultura e cultura da interface do usuário é o mesmo para idiomas bidirecionais, assim como para outros idiomas. Para obter mais informações, consulte [classes específicas de cultura para Windows forms e web forms globais](/visualstudio/ide/culture-specific-classes-for-global-windows-forms-and-web-forms).  
  
## <a name="righttoleft-and-righttoleftlayout-properties"></a>Propriedades RightToLeft e RightToLeftLayout  
 A base <xref:System.Windows.Forms.Control> classe, da qual os formulários derivam, inclui um <xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade que você pode definir para alterar a ordem de leitura de um formulário e seus controles. Se você definir o formulário <xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade, por controles padrão no formulário herdarão essa configuração. No entanto, você também pode definir o <xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade individualmente na maioria dos controles. Consulte também [como: Exibir o texto da direita para a esquerda nos Windows Forms para globalização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).  
  
 O efeito do <xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade pode diferir de um controle para outro. Em alguns controles a propriedade somente define a ordem de leitura, como mostra a <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> e <xref:System.Windows.Forms.ToolTip> controles. Em outros controles, o <xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade altera a ordem de leitura e de layout. Isso inclui o <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.CheckBox> controles. Outros controles exigem que o <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> propriedade ser aplicada para espelhar o seu layout da direita para esquerda. A tabela a seguir fornece detalhes sobre como o <xref:System.Windows.Forms.Control.RightToLeft%2A> e <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> propriedades afetam controles individuais dos Windows Forms.  
  
|Controle/componente|Propriedade RightToLeft|Efeito da propriedade RightToLeftLayout|Exige espelhamento?|  
|------------------------|------------------------------------|------------------------------------------|-------------------------|  
|<xref:System.Windows.Forms.Button>|Define o sentido da leitura RTL. Inverte <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>, e <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Sem efeito|Não|  
|<xref:System.Windows.Forms.CheckBox>|A caixa de seleção é exibida à direita do texto|Sem efeito|Não|  
|<xref:System.Windows.Forms.CheckedListBox>|Todas as caixas de seleção são exibidas à direita do texto|Sem efeito|Não|  
|<xref:System.Windows.Forms.ColorDialog>|Não é afetado; depende do idioma do sistema operacional|Sem efeito|Não|  
|<xref:System.Windows.Forms.ComboBox>|Itens no controle de caixa de combinação são alinhadas à direita|Sem efeito|Não|  
|<xref:System.Windows.Forms.ContextMenu>|É exibido alinhado à direita com sentido da leitura RTL|Sem efeito|Não|  
|<xref:System.Windows.Forms.DataGrid>|É exibido alinhado à direita com sentido da leitura RTL|Sem efeito|Não|  
|<xref:System.Windows.Forms.DataGridView>|Afeta a ordem e controle de layout de leitura RTL|Sem efeito|Não|  
|<xref:System.Windows.Forms.DateTimePicker>|Não é afetado; depende do idioma do sistema operacional|Espelha o controle|Sim|  
|<xref:System.Windows.Forms.DomainUpDown>|Alinha à esquerda os botões para cima e para baixo|Sem efeito|Não|  
|<xref:System.Windows.Forms.ErrorProvider>|Sem suporte|Sem efeito|Não|  
|<xref:System.Windows.Forms.FontDialog>|Depende do idioma do sistema operacional|Sem efeito|Não|  
|<xref:System.Windows.Forms.Form>|Define o sentido da leitura RTL e inverte as barras de rolagem|Espelha o formulário|Sim|  
|<xref:System.Windows.Forms.GroupBox>|A legenda é exibida alinhada à direita. Controles filho podem herdar esta propriedade.|Use um <xref:System.Windows.Forms.TableLayoutPanel> dentro do controle para o espelhamento da direita para esquerda suporte|Não|  
|<xref:System.Windows.Forms.HScrollBar>|Começa com a caixa de rolagem (thumb) alinhada à direita|Sem efeito|Não|  
|<xref:System.Windows.Forms.ImageList>|Não necessário|Sem efeito|Não|  
|<xref:System.Windows.Forms.Label>|Exibido alinhado à direita. Inverte <xref:System.Windows.Forms.Label.TextAlign%2A> e <xref:System.Windows.Forms.Label.ImageAlign%2A>|Sem efeito|Não|  
|<xref:System.Windows.Forms.LinkLabel>|Exibido alinhado à direita. Inverte <xref:System.Windows.Forms.Label.TextAlign%2A> e <xref:System.Windows.Forms.Label.ImageAlign%2A>|Sem efeito|Não|  
|<xref:System.Windows.Forms.ListBox>|Itens são alinhados à direita|Sem efeito|Não|  
|<xref:System.Windows.Forms.ListView>|Define o sentido da leitura RTL; elementos permanecem alinhados à esquerda|Espelha o controle|Sim|  
|<xref:System.Windows.Forms.MainMenu>|Exibido alinhado à direita com sentido da leitura RTL em tempo de execução (não em tempo de design)|Sem efeito|Não|  
|<xref:System.Windows.Forms.MaskedTextBox>|Exibe o texto da direita para a esquerda.|Sem efeito|Não|  
|<xref:System.Windows.Forms.MonthCalendar>|Não é afetado; depende do idioma do sistema operacional|Espelha o controle|Sim|  
|<xref:System.Windows.Forms.NotifyIcon>|Sem suporte|Sem suporte|Não|  
|<xref:System.Windows.Forms.NumericUpDown>|Botões para cima e para baixo são alinhados à esquerda|Sem efeito|Não|  
|<xref:System.Windows.Forms.OpenFileDialog>|Em sistemas operacionais da direita para esquerda, a configuração do formulário que contém <xref:System.Windows.Forms.Control.RightToLeft> propriedade para <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> localiza a caixa de diálogo |Sem efeito|Não|  
|<xref:System.Windows.Forms.PageSetupDialog>|Não é afetado; depende do idioma do sistema operacional|Sem efeito|Não|  
|<xref:System.Windows.Forms.Panel>|Controles filho podem herdar esta propriedade|Use <xref:System.Windows.Forms.TableLayoutPanel> dentro do controle para suporte|Sim|  
|<xref:System.Windows.Forms.PictureBox>|Sem suporte|Sem efeito|Não|  
|<xref:System.Windows.Forms.PrintDialog>|Não é afetado; depende do idioma do sistema operacional|Sem efeito|Não|  
|<xref:System.Drawing.Printing.PrintDocument>|A barra de rolagem vertical torna-se alinhada à esquerda e a barra de rolagem horizontal começa da esquerda|Sem efeito|Não|  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Sem suporte|Sem suporte|Não|  
|<xref:System.Windows.Forms.ProgressBar>|Não afetado por esta propriedade|Espelha o controle|Sim|  
|<xref:System.Windows.Forms.RadioButton>|Botão de opção é exibido à direita do texto|Sem efeito|Não|  
|<xref:System.Windows.Forms.RichTextBox>|Elementos de controle que incluem texto são exibidos da direita para a esquerda com sentido da leitura RTL|Sem efeito|Não|  
|<xref:System.Windows.Forms.SaveFileDialog>|Não é afetado; depende do idioma do sistema operacional|Sem efeito|Não|  
|<xref:System.Windows.Forms.SplitContainer>|Layout do painel é invertido; barra de rolagem vertical aparece à esquerda; barra de rolagem horizontal começa da direita|Use um <xref:System.Windows.Forms.TableLayoutPanel> para espelhar a ordem dos controles filho|Não|  
|<xref:System.Windows.Forms.Splitter>|Sem suporte|Sem efeito|Não|  
|<xref:System.Windows.Forms.StatusBar>|Não há suporte para; Use <xref:System.Windows.Forms.StatusStrip> em vez disso|Nenhum efeito; Use <xref:System.Windows.Forms.StatusStrip> em vez disso|Não|  
|<xref:System.Windows.Forms.TabControl>|Não afetado por esta propriedade|Espelha o controle|Sim|  
|<xref:System.Windows.Forms.TextBox>|Exibe o texto da direita para a esquerda com sentido da leitura RTL|Sem efeito|Não|  
|<xref:System.Windows.Forms.Timer>|Não necessário|Não necessário|Não|  
|<xref:System.Windows.Forms.ToolBar>|Não é afetado por essa propriedade; Use <xref:System.Windows.Forms.ToolStrip> em vez disso|Nenhum efeito; Use <xref:System.Windows.Forms.ToolStrip> em vez disso|Sim|  
|<xref:System.Windows.Forms.ToolTip>|Define o sentido da leitura RTL|Sem efeito|Não|  
|<xref:System.Windows.Forms.TrackBar>|A rolagem ou rastreamento começa da direita; Quando <xref:System.Windows.Forms.TrackBar.Orientation%2A> é vertical, a marcação ocorre da direita|Sem efeito|Não|  
|<xref:System.Windows.Forms.TreeView>|Define somente sentido da leitura RTL|Espelha o controle|Sim|  
|<xref:System.Windows.Forms.UserControl>|Barra de rolagem vertical aparece à esquerda; barra de rolagem horizontal tem o ícone à direita|Não há suporte direto; usar um <xref:System.Windows.Forms.TableLayoutPanel>|Não|  
|<xref:System.Windows.Forms.VScrollBar>|Exibido no lado esquerdo em vez do lado direito de controles roláveis|Sem efeito|Não|  
  
## <a name="encoding"></a>Codificando  
 Windows Forms oferece suporte a Unicode, para que você possa incluir qualquer caractere definido quando você cria seus aplicativos bi-direcionais. No entanto, nem todos os controles dos Windows Forms oferecem suporte a Unicode em todas as plataformas. Para obter mais informações, consulte [Codificação e Globalização dos Windows Forms](encoding-and-windows-forms-globalization.md).  
  
## <a name="gdi"></a>GDI+  
 Você pode usar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para desenhar texto com sentido da leitura da direita para a esquerda. O <xref:System.Drawing.Graphics.DrawString%2A> dá suporte ao método, que é usado para desenhar o texto, uma `StringFormat` parâmetro que pode ser definido para o <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> membro do <xref:System.Drawing.StringFormatFlags> enumeração para inverter o ponto de origem do texto.  
  
## <a name="common-dialog-boxes"></a>Caixas de diálogo comuns  
 Ferramentas do sistema, como a caixa de diálogo Abrir arquivo estão sob o controle do Windows. Elas herdam os elementos de linguagem do sistema operacional. Se você estiver usando uma versão do Windows com as configurações de idioma correto, essas caixas de diálogo funcionarão corretamente com idiomas bidirecionais.  
  
 Da mesma forma, caixas de mensagem passam pelo sistema operacional e fornecem suporte a texto bidirecional. As legendas nos botões da caixa de mensagem baseiam-se na configuração de idioma atual. Por padrão, as caixas de mensagens não use sentido da leitura da direita para a esquerda, mas você pode especificar um parâmetro para alterar o sentido da leitura quando as caixas de mensagem são exibidas.  
  
## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, Scrollbars e ScrollableControl  
 Atualmente, há uma limitação nos Windows Forms que impede que todas as classes derivadas <xref:System.Windows.Forms.ScrollableControl> funcione corretamente quando ambos <xref:System.Windows.Forms.Control.RightToLeft%2A> está habilitado e <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> é definido como <xref:System.Windows.Forms.RightToLeft.Yes>. Por exemplo, digamos que você coloque um controle, como <xref:System.Windows.Forms.Panel>— ou uma classe de contêiner derivado <xref:System.Windows.Forms.Panel> (como <xref:System.Windows.Forms.FlowLayoutPanel> ou <xref:System.Windows.Forms.TableLayoutPanel>) — em seu formulário. Se você definir <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> no contêiner para <xref:System.Windows.Forms.RightToLeft.Yes> e, em seguida, defina as <xref:System.Windows.Forms.Control.Anchor%2A> propriedade em um ou mais dos controles dentro do contêiner para <xref:System.Windows.Forms.AnchorStyles.Right>, então nenhuma barra de rolagem aparecerá. A classe derivada de <xref:System.Windows.Forms.ScrollableControl> age como se <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> foram definidos como <xref:System.Windows.Forms.RightToLeft.No>.  
  
 Atualmente, a única solução alternativa é aninhar os <xref:System.Windows.Forms.ScrollableControl> dentro de outro <xref:System.Windows.Forms.ScrollableControl>. Por exemplo, se você precisar <xref:System.Windows.Forms.TableLayoutPanel> para trabalhar nessa situação, você pode colocá-lo dentro de um <xref:System.Windows.Forms.Panel> controle e defina <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> sobre o <xref:System.Windows.Forms.Panel> para <xref:System.Windows.Forms.RightToLeft.Yes>.  
  
## <a name="mirroring"></a>Espelhamento  
 *Espelhamento* refere-se a inverter o layout dos elementos de interface do usuário para que eles fluam da direita para a esquerda. No Windows Form espelhado, por exemplo, os botões minimizar, maximizar e fechar aparecem mais à esquerda na barra de título, não mais à direita.  
  
 Configurar um formulário ou do controle <xref:System.Windows.Forms.Control.RightToLeft%2A> propriedade para `true` inverte a ordem de leitura de elementos em um formulário, mas essa configuração não inverte o layout para direita para esquerda — isto é, não causa espelhamento. Por exemplo, a configuração dessa propriedade não move os botões **minimizar**, **maximizar** e **fechar** na barra de título do formulário para o lado esquerdo do formulário. Da mesma forma, alguns controles, como o <xref:System.Windows.Forms.TreeView> , requerem espelhamento para alterar sua exibição para ser apropriado para árabe ou hebraico. Você pode espelhar estes controles Configurando a <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> propriedade.  
  
 Você pode criar versões espelhadas dos seguintes controles:  
  
- <xref:System.Windows.Forms.ColumnHeader.ListView%2A>  
  
- <xref:System.Windows.Forms.Panel>  
  
- <xref:System.Windows.Forms.StatusBar>  
  
- <xref:System.Windows.Forms.TabControl>  
  
- <xref:System.Windows.Forms.TabPage>  
  
- <xref:System.Windows.Forms.ToolBar>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 Alguns controles são lacrados. Portanto, você não pode derivar um novo controle deles. Isso inclui o <xref:System.Windows.Forms.ImageList> e <xref:System.Windows.Forms.ProgressBar> controles.  
  
## <a name="see-also"></a>Consulte também

- [Suporte bidirecional para aplicativos Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
- [Globalizando aplicativos dos Windows Forms](globalizing-windows-forms.md)

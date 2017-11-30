---
title: "Controles dos Windows Forms por função"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c49c42b02511fea66c88544bf689b2b05e788ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-controls-by-function"></a>Controles dos Windows Forms por função
O Windows Forms oferece controles e componentes que executam várias funções. A tabela a seguir lista os controles e componentes dos Windows Forms de acordo com a função geral. Além disso, quando há vários controles que têm a mesma função, o controle recomendado é listado com uma observação sobre o controle que foi substituído por ele. Em uma tabela separada posterior, os controles substituídos são listados com suas substituições recomendadas.  
  
> [!NOTE]
>  As tabelas a seguir não listam todos os controles ou componentes que você pode usar nos Windows Forms. Para obter uma lista mais abrangente, consulte [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Controles e componentes recomendados  
  
|Função|Controle|Descrição|  
|--------------|-------------|-----------------|  
|Exibição de dados|Controle <xref:System.Windows.Forms.DataGridView>|O <xref:System.Windows.Forms.DataGridView> controle fornece uma tabela personalizável para exibir dados. O <xref:System.Windows.Forms.DataGridView> classe permite que a personalização de células, linhas, colunas e bordas. **Observação:** o <xref:System.Windows.Forms.DataGridView> controle fornece vários recursos básicos e avançados que estão faltando no <xref:System.Windows.Forms.DataGrid> controle. Para obter mais informações, consulte [Diferenças entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Vinculação de dados e navegação|<xref:System.Windows.Forms.BindingSource>componente|Simplifica a associação de controles em um formulário a dados, fornecendo gerenciamento de moeda, notificação de alteração e outros serviços.|  
||Controle <xref:System.Windows.Forms.BindingNavigator>|Fornece uma interface do tipo de barra de ferramentas para navegar e manipular dados em um formulário.|  
|Edição de texto|Controle <xref:System.Windows.Forms.TextBox>|Exibe o texto inserido em tempo de design que pode ser editado por usuários em tempo de execução ou ser modificado programaticamente.|  
||Controle <xref:System.Windows.Forms.RichTextBox>|Permite que o texto seja exibido formatado em texto sem formatação ou em RTF (Formato Rich Text).|  
||Controle <xref:System.Windows.Forms.MaskedTextBox>|Restringe o formato da entrada do usuário|  
|Exibição de informações (somente leitura)|Controle <xref:System.Windows.Forms.Label>|Exibe o texto que os usuários não podem editar diretamente.|  
||Controle <xref:System.Windows.Forms.LinkLabel>|Exibe o texto como um link com estilo da Web e dispara um evento quando o usuário clica no texto especial. Normalmente, o texto é um link para outra janela ou site.|  
||Controle <xref:System.Windows.Forms.StatusStrip>|Exibe informações sobre o estado atual do aplicativo usando uma área com quadros, geralmente na parte inferior de um formulário pai.|  
||Controle <xref:System.Windows.Forms.ProgressBar>|Exibe o progresso atual de uma operação para o usuário.|  
|Exibição de página da Web|Controle <xref:System.Windows.Forms.WebBrowser>|Permite ao usuário navegar em páginas da Web dentro do seu formulário.|  
|Seleção de uma lista|Controle <xref:System.Windows.Forms.CheckedListBox>|Exibe uma lista rolável de itens, cada um deles acompanhado por uma caixa de seleção.|  
||Controle <xref:System.Windows.Forms.ComboBox>|Exibe uma lista suspensa de itens.|  
||Controle <xref:System.Windows.Forms.DomainUpDown>|Exibe uma lista de itens de texto que os usuários podem percorrer usando os botões para cima e para baixo.|  
||Controle <xref:System.Windows.Forms.ListBox>|Exibe uma lista de texto e itens gráficos (ícones).|  
||Controle <xref:System.Windows.Forms.ListView>|Exibe os itens em um dos quatro modos de exibição diferentes. Os modos de exibição incluem somente texto, texto com ícones pequenos, texto com ícones grandes e exibição de detalhes.|  
||Controle <xref:System.Windows.Forms.NumericUpDown>|Exibe uma lista de numerais que os usuários podem percorrer usando os botões para cima e para baixo.|  
||Controle <xref:System.Windows.Forms.TreeView>|Exibe uma coleção hierárquica de objetos de nó que podem consistir em texto com caixas de seleção opcionais ou ícones.|  
|Exibição de gráficos|Controle <xref:System.Windows.Forms.PictureBox>|Exibe arquivos gráficos, como bitmaps e ícones, em um quadro.|  
|Armazenamento de gráficos|Controle <xref:System.Windows.Forms.ImageList>|Serve como um repositório de imagens. <xref:System.Windows.Forms.ImageList>as imagens que eles contêm e os controles podem ser reutilizadas de um aplicativo para o próximo.|  
|Configuração do valor|Controle <xref:System.Windows.Forms.CheckBox>|Exibe uma caixa de seleção e um rótulo de texto. Geralmente, é usado para definir opções.|  
||Controle <xref:System.Windows.Forms.CheckedListBox>|Exibe uma lista rolável de itens, cada um deles acompanhado por uma caixa de seleção.|  
||Controle <xref:System.Windows.Forms.RadioButton>|Exibe um botão que pode ser ativado ou desativado.|  
||Controle <xref:System.Windows.Forms.TrackBar>|Permite aos usuários definir valores em uma escala movendo um "controle de posição" ao longo da escala.|  
|Configuração de data|Controle <xref:System.Windows.Forms.DateTimePicker>|Exibe um calendário gráfico para permitir que os usuários selecionem uma data ou hora.|  
||Controle <xref:System.Windows.Forms.MonthCalendar>|Exibe um calendário gráfico para permitir que os usuários selecionem um intervalo de datas.|  
|Caixas de diálogo|Controle <xref:System.Windows.Forms.ColorDialog>|Exibe a caixa de diálogo do seletor de cor que permite que os usuários definam a cor de um elemento de interface.|  
||Controle <xref:System.Windows.Forms.FontDialog>|Exibe uma caixa de diálogo que permite que os usuários definam uma fonte e seus atributos.|  
||Controle <xref:System.Windows.Forms.OpenFileDialog>|Exibe uma caixa de diálogo que permite que os usuários naveguem até um arquivo e o selecionem.|  
||Controle <xref:System.Windows.Forms.PrintDialog>|Exibe uma caixa de diálogo que permite que os usuários selecionem uma impressora e definam seus atributos.|  
||Controle <xref:System.Windows.Forms.PrintPreviewDialog>|Exibe uma caixa de diálogo que exibe como um controle <xref:System.Drawing.Printing.PrintDocument> componente aparecerá quando impresso.|  
||Controle <xref:System.Windows.Forms.FolderBrowserDialog>|Exibe uma caixa de diálogo que permite que os usuários naveguem, criem e, eventualmente, selecionem uma pasta|  
||Controle <xref:System.Windows.Forms.SaveFileDialog>|Exibe uma caixa de diálogo que permite que os usuários salvem um arquivo.|  
|Controles de menu|Controle <xref:System.Windows.Forms.MenuStrip>|Cria menus personalizados. **Observação:** o <xref:System.Windows.Forms.MenuStrip> foi projetado para substituir o <xref:System.Windows.Forms.MainMenu> controle.|  
||Controle <xref:System.Windows.Forms.ContextMenuStrip>|Cria menus de contexto personalizados. **Observação:** o <xref:System.Windows.Forms.ContextMenuStrip> foi projetado para substituir o <xref:System.Windows.Forms.ContextMenu> controle.|  
|Comandos|Controle <xref:System.Windows.Forms.Button>|Inicia, para ou interrompe um processo.|  
||Controle <xref:System.Windows.Forms.LinkLabel>|Exibe o texto como um link com estilo da Web e dispara um evento quando o usuário clica no texto especial. Normalmente, o texto é um link para outra janela ou site.|  
||Controle <xref:System.Windows.Forms.NotifyIcon>|Exibe um ícone na área de notificação de status da barra de tarefas que representa um aplicativo em execução em segundo plano.|  
||Controle <xref:System.Windows.Forms.ToolStrip>|Cria barras de ferramentas que podem ter a aparência do Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer ou uma aparência personalizada, com ou sem temas e com suporte para estouro e reordenação de itens em tempo de execução. **Observação:** o <xref:System.Windows.Forms.ToolStrip> controle foi projetado para substituir o <xref:System.Windows.Forms.ToolBar> controle.|  
|Ajuda do usuário|<xref:System.Windows.Forms.HelpProvider>componente|Fornece Ajuda pop-up ou online para os controles.|  
||<xref:System.Windows.Forms.ToolTip>componente|Fornece uma janela pop-up que exibe uma breve descrição da finalidade do controle quando o usuário deixa o ponteiro sobre o controle.|  
|Agrupando outros controles|Controle <xref:System.Windows.Forms.Panel>|Agrupa um conjunto de controles em um quadro rolável sem rótulo.|  
||Controle <xref:System.Windows.Forms.GroupBox>|Agrupa um conjunto de controles (como botões de opção) em um quadro não rolável rotulado.|  
||Controle <xref:System.Windows.Forms.TabControl>|Fornece uma página com guias para organizar e acessar objetos agrupados com eficiência.|  
||Controle <xref:System.Windows.Forms.SplitContainer>|Fornece dois painéis separados por uma barra móvel. **Observação:** o <xref:System.Windows.Forms.SplitContainer> controle foi projetado para substituir o <xref:System.Windows.Forms.Splitter> controle.|  
||Controle <xref:System.Windows.Forms.TableLayoutPanel>|Representa um painel que dispõe de forma dinâmica o conteúdo em uma grade composta por linhas e colunas.|  
||Controle <xref:System.Windows.Forms.FlowLayoutPanel>|Representa um painel que dispõe de forma dinâmica o conteúdo horizontal ou verticalmente.|  
|Áudio|Controle <xref:System.Media.SoundPlayer>|Reproduz arquivos de som no formato .wav. Os sons podem ser carregados ou executados de forma assíncrona.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Controles e componentes substituídos por função  
  
|Função|Controle substituído|Substituição recomendada|  
|--------------|------------------------|-----------------------------|  
|Exibição de dados|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Exibição de informações (controles somente leitura)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Controles de menu|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Comandos|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Layout de formulários|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Consulte também  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)

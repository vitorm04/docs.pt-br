---
title: 'Instruções passo a passo: organizando conteúdo WPF em Windows Forms na hora do design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: 373a7f977a9dad59cd40fd29fdd39c8fc6996ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529296"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>Instruções passo a passo: organizando conteúdo WPF em Windows Forms na hora do design
Esta instrução passo a passo mostra como usar os recursos de layout dos Windows Forms, como ancoragem e guias de alinhamento para organizar controles do WPF (Windows Presentation Foundation).  
  
 Nesta instrução passo a passo, as seguintes tarefas serão executadas:  
  
-   Crie o projeto.  
  
-   Crie o controle WPF.  
  
-   Hospede controles WPF em um painel de layout.  
  
-   Use guias de alinhamento para alinhar controles WPF.  
  
-   Ancore e encaixe controles WPF.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto dos Windows Forms.  
  
> [!NOTE]
>  Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
-   Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `ArrangeElementHost`.  
  
## <a name="creating-the-wpf-control"></a>Criando o controle WPF  
 Depois de adicionar um controle WPF ao projeto, você pode organizá-lo no formulário.  
  
#### <a name="to-create-wpf-controls"></a>Para criar controles WPF  
  
1.  Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao projeto. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  No modo de exibição de Design, verifique se `UserControl1` está selecionado. Para obter mais informações, consulte [Como Selecionar e Mover Elementos na Superfície de Design](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades `200`.  
  
4.  Definir o valor de <xref:System.Windows.Controls.Control.Background%2A> propriedade `Blue`.  
  
5.  Compile o projeto.  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>Hospedando controles WPF em um painel de layout  
 Você pode usar controles WPF nos painéis de layout da mesma maneira que você usa outros controles dos Windows Forms.  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>Para hospedar controles WPF em um painel de layout  
  
1.  Abra `Form1` no Designer de Formulários do Windows.  
  
2.  No **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle para o formulário.  
  
3.  Sobre o <xref:System.Windows.Forms.TableLayoutPanel> painel de marcas inteligentes do controle, selecione **remover a última linha**.  
  
4.  Redimensionar o <xref:System.Windows.Forms.TableLayoutPanel> controle para uma maior largura e altura.  
  
5.  No **caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` na primeira célula do <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
     A instância do `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.  
  
6.  No **caixa de ferramentas**, clique duas vezes em `UserControl1` para criar outra instância na segunda célula do <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
7.  Na janela **Estrutura de Tópicos do Documento**, selecione `tableLayoutPanel1`. Para obter mais informações, consulte a [Janela de Estrutura de Tópicos do Documento](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).  
  
8.  No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Control.Padding%2A> propriedade `10, 10, 10, 10`.  
  
     Ambos <xref:System.Windows.Forms.Integration.ElementHost> controles são redimensionados para caber no novo layout.  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>Usando guias de alinhamento para alinhar controles WPF  
 Guias de alinhamento permitem fácil alinhamento de controles em um formulário. Você também pode usar guias de alinhamento para alinhar os controles WPF. Para obter mais informações, consulte [Instruções passo a passo: organizando controles nos Windows Forms usando guias de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>Para usar guias de alinhamento para alinhar controles WPF  
  
1.  Do **caixa de ferramentas**, arraste uma instância de `UserControl1` para o formulário e coloque-o no espaço abaixo o <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
     A instância do `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost3`.  
  
2.  Usando guias de alinhamento, alinhe a borda esquerda do `elementHost3` com a borda esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
3.  Usando guias de alinhamento, tamanho `elementHost3` para a mesma largura que o <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
4.  Mover `elementHost3` em direção a <xref:System.Windows.Forms.TableLayoutPanel> controle até que apareça uma snapline de centro entre os controles.  
  
5.  Na janela **Propriedades**, defina o valor da propriedade Margem como `20, 20, 20, 20`.  
  
6.  Mover o `elementHost3` fora o <xref:System.Windows.Forms.TableLayoutPanel> controlar até que a snapline do centro apareça novamente. A guia de alinhamento central agora indica uma margem de 20.  
  
7.  Mova `elementHost3` para a direita, até que sua borda esquerda se alinhe com a borda esquerda de `elementHost1`.  
  
8.  Altere a largura de `elementHost3` até que a borda direita alinhe com a borda direita de `elementHost2`.  
  
## <a name="anchoring-and-docking-wpf-controls"></a>Ancorando e encaixando controles WPF  
 Um controle WPF hospedado em um formulário tem o mesmo comportamento de ancoragem e encaixe que outros controles dos Windows Forms.  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>Para ancorar e encaixar controles WPF  
  
1.  Selecione `elementHost1`.  
  
2.  No **propriedades** janela, defina o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade **superior, inferior, esquerda, direita**.  
  
3.  Redimensionar o <xref:System.Windows.Forms.TableLayoutPanel> controle para um tamanho maior.  
  
     O controle `elementHost1` será redimensionado para preencher a célula.  
  
4.  Selecione `elementHost2`.  
  
5.  No **propriedades** janela, defina o valor da <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     O controle `elementHost2` será redimensionado para preencher a célula.  
  
6.  Selecione o <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
7.  Defina o valor de seu <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Top>.  
  
8.  Selecione `elementHost3`.  
  
9. Defina o valor de seu <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     O controle `elementHost3` será redimensionado para preencher o espaço restante no formulário.  
  
10. Redimensione o formulário.  
  
     Todos os três <xref:System.Windows.Forms.Integration.ElementHost> controles redimensionam adequadamente.  
  
     Para obter mais informações, consulte [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Como alinhar um controle às bordas de formulários no tempo de design](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Usando Controles do WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)

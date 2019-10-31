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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9062a3da9a6020762114702b6cce6b42414ab92d
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197448"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>Walkthrough: organizar o conteúdo do WPF em Windows Forms em tempo de design

Este artigo mostra como usar os recursos de layout de Windows Forms, como ancoragem e snaplines, para organizar os controles de Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Prerequisites

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-the-project"></a>Criar o projeto

Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou Visual chamado `ArrangeElementHost`.

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-the-wpf-control"></a>Criar o controle WPF

Depois de adicionar um controle WPF ao projeto, você pode organizá-lo no formulário.

1. Adicione um novo <xref:System.Windows.Controls.UserControl> do WPF ao projeto. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado.

3. Na janela **Propriedades** , defina o valor das propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

4. Defina o valor da propriedade <xref:System.Windows.Controls.Control.Background%2A> como **azul**.

5. Compile o projeto.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Hospedar controles WPF em um painel de layout

Você pode usar controles WPF nos painéis de layout da mesma maneira que você usa outros controles dos Windows Forms.

1. Abra `Form1` no Designer de Formulários do Windows.

2. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> para o formulário.

3. No painel de marcas inteligentes do controle de <xref:System.Windows.Forms.TableLayoutPanel>, selecione **remover última linha**.

4. Redimensione o controle de <xref:System.Windows.Forms.TableLayoutPanel> para uma largura e altura maiores.

5. Na **caixa de ferramentas**, clique duas vezes em `UserControl1` para criar uma instância de `UserControl1` na primeira célula do controle de <xref:System.Windows.Forms.TableLayoutPanel>.

   A instância do `UserControl1` é hospedada em um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost1`.

6. Na **caixa de ferramentas**, clique duas vezes em `UserControl1` para criar outra instância na segunda célula do controle de <xref:System.Windows.Forms.TableLayoutPanel>.

7. Na janela **Estrutura de Tópicos do Documento**, selecione `tableLayoutPanel1`.

8. Na janela **Propriedades** , defina o valor da propriedade <xref:System.Windows.Forms.Control.Padding%2A> como **10, 10, 10, 10**.

   Ambos os controles <xref:System.Windows.Forms.Integration.ElementHost> são redimensionados para caber no novo layout.

## <a name="use-snaplines-to-align-wpf-controls"></a>Usar snaplines para alinhar controles WPF

Guias de alinhamento permitem fácil alinhamento de controles em um formulário. Você também pode usar guias de alinhamento para alinhar os controles WPF. Para obter mais informações, consulte [Instruções passo a passo: organizando controles nos Windows Forms usando guias de alinhamento](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

1. Na **caixa de ferramentas**, arraste uma instância de `UserControl1` para o formulário e coloque-a no espaço abaixo do controle de <xref:System.Windows.Forms.TableLayoutPanel>.

   A instância do `UserControl1` é hospedada em um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost3`.

2. Usando Snaplines, alinhe a borda esquerda de `elementHost3` com a borda esquerda do controle <xref:System.Windows.Forms.TableLayoutPanel>.

3. Usando Snaplines, o tamanho `elementHost3` para a mesma largura que o controle de <xref:System.Windows.Forms.TableLayoutPanel>.

4. Mova `elementHost3` para o controle de <xref:System.Windows.Forms.TableLayoutPanel> até que uma SnapLine de centro apareça entre os controles.

5. Na janela **Propriedades** , defina o valor da propriedade Margin como **20, 20, 20, 20**.

6. Mova o `elementHost3` para fora do controle de <xref:System.Windows.Forms.TableLayoutPanel> até que a SnapLine do centro apareça novamente. A guia de alinhamento central agora indica uma margem de 20.

7. Mova `elementHost3` para a direita até que sua borda esquerda fique alinhada com a borda esquerda de `elementHost1`.

8. Altere a largura de `elementHost3` até que a borda direita alinhe com a borda direita de `elementHost2`.

## <a name="anchor-and-dock-wpf-controls"></a>Ancorar e encaixar controles WPF

Um controle WPF hospedado em um formulário tem o mesmo comportamento de ancoragem e encaixe que outros controles dos Windows Forms.

1. Selecione `elementHost1`.

2. Na janela **Propriedades** , defina a propriedade <xref:System.Windows.Forms.Control.Anchor%2A> como **superior, inferior, esquerda, direita**.

3. Redimensione o controle de <xref:System.Windows.Forms.TableLayoutPanel> para um tamanho maior.

   O controle `elementHost1` será redimensionado para preencher a célula.

4. Selecione `elementHost2`.

5. Na janela **Propriedades** , defina o valor da propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.

   O controle `elementHost2` será redimensionado para preencher a célula.

6. Selecione o controle <xref:System.Windows.Forms.TableLayoutPanel>.

7. Defina o valor de sua propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Top>.

8. Selecione `elementHost3`.

9. Defina o valor de sua propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.

   O controle `elementHost3` será redimensionado para preencher o espaço restante no formulário.

10. Redimensione o formulário.

    Todos os três controles de <xref:System.Windows.Forms.Integration.ElementHost> redimensionam adequadamente.

    Para obter mais informações, consulte [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Como alinhar um controle às bordas de formulários no tempo de design](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migração e Interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)

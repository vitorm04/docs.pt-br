---
title: 'Passo a passo: organizar conteúdo WPF no Windows Forms na hora do design'
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
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658518"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>Passo a passo: Organizar o conteúdo do WPF em Windows Forms em tempo de design

Este artigo mostra como usar os recursos de layout de Windows Forms, como ancoragem e snaplines, para organizar os controles de Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Pré-requisitos

É necessário o Visual Studio para concluir este passo a passo.

## <a name="create-the-project"></a>Criar o projeto

Abra o Visual Studio e crie um novo projeto de aplicativo Windows Forms em Visual Basic C# ou `ArrangeElementHost`Visual chamado.

> [!NOTE]
> Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.

## <a name="create-the-wpf-control"></a>Criar o controle WPF

Depois de adicionar um controle WPF ao projeto, você pode organizá-lo no formulário.

1. Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao projeto. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, confira [Passo a passo: Criando novo conteúdo do WPF em Windows Forms em tempo](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de design.

2. No modo de exibição de Design, verifique se `UserControl1` está selecionado.

3. Na janela **Propriedades** , defina o valor das <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> como **200**.

4. Defina o valor da <xref:System.Windows.Controls.Control.Background%2A> Propriedade como **azul**.

5. Compile o projeto.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Hospedar controles WPF em um painel de layout

Você pode usar controles WPF nos painéis de layout da mesma maneira que você usa outros controles dos Windows Forms.

1. Abra `Form1` no Designer de Formulários do Windows.

2. Na **caixa de ferramentas**, arraste <xref:System.Windows.Forms.TableLayoutPanel> um controle para o formulário.

3. No painel de marcas inteligentes do controle,selecioneremoverúltimalinha.<xref:System.Windows.Forms.TableLayoutPanel>

4. Redimensione o <xref:System.Windows.Forms.TableLayoutPanel> controle para uma largura e altura maiores.

5. Na **caixa de ferramentas**, `UserControl1` clique duas vezes para criar uma instância do `UserControl1` na primeira célula do <xref:System.Windows.Forms.TableLayoutPanel> controle.

   A instância do `UserControl1` é hospedada em um <xref:System.Windows.Forms.Integration.ElementHost> novo controle `elementHost1`chamado.

6. Na **caixa de ferramentas**, clique `UserControl1` duas vezes para criar outra instância na <xref:System.Windows.Forms.TableLayoutPanel> segunda célula do controle.

7. Na janela **Estrutura de Tópicos do Documento**, selecione `tableLayoutPanel1`.

8. Na janela **Propriedades** , defina o valor da <xref:System.Windows.Forms.Control.Padding%2A> Propriedade como **10, 10, 10, 10**.

   Ambos <xref:System.Windows.Forms.Integration.ElementHost> os controles são redimensionados para caber no novo layout.

## <a name="use-snaplines-to-align-wpf-controls"></a>Usar snaplines para alinhar controles WPF

Guias de alinhamento permitem fácil alinhamento de controles em um formulário. Você também pode usar guias de alinhamento para alinhar os controles WPF. Para obter mais informações, confira [Passo a passo: Organizando controles em Windows Forms usando Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

1. Na **caixa de ferramentas**, arraste uma instância `UserControl1` do para o formulário e coloque-a no espaço abaixo do <xref:System.Windows.Forms.TableLayoutPanel> controle.

   A instância do `UserControl1` é hospedada em um <xref:System.Windows.Forms.Integration.ElementHost> novo controle `elementHost3`chamado.

2. Usando Snaplines, alinhe a borda esquerda de `elementHost3` com a borda esquerda do <xref:System.Windows.Forms.TableLayoutPanel> controle.

3. Usando Snaplines, dimensione o tamanho `elementHost3` para a mesma largura do <xref:System.Windows.Forms.TableLayoutPanel> controle.

4. Mover `elementHost3` para o <xref:System.Windows.Forms.TableLayoutPanel> controle até que uma SnapLine central apareça entre os controles.

5. Na janela **Propriedades** , defina o valor da propriedade Margin como **20, 20, 20, 20**.

6. Mova a `elementHost3` distância <xref:System.Windows.Forms.TableLayoutPanel> do controle até que a SnapLine do centro seja exibida novamente. A guia de alinhamento central agora indica uma margem de 20.

7. Mova `elementHost3` para a direita até que sua borda esquerda fique alinhada com a borda `elementHost1`esquerda de.

8. Altere a largura de `elementHost3` até que a borda direita alinhe com a borda direita de `elementHost2`.

## <a name="anchor-and-dock-wpf-controls"></a>Ancorar e encaixar controles WPF

Um controle WPF hospedado em um formulário tem o mesmo comportamento de ancoragem e encaixe que outros controles dos Windows Forms.

1. Selecione `elementHost1`.

2. Na janela **Propriedades** , defina a <xref:System.Windows.Forms.Control.Anchor%2A> Propriedade como **superior, inferior, esquerda, direita**.

3. Redimensione o <xref:System.Windows.Forms.TableLayoutPanel> controle para um tamanho maior.

   O controle `elementHost1` será redimensionado para preencher a célula.

4. Selecione `elementHost2`.

5. Na janela **Propriedades** , defina o valor da <xref:System.Windows.Forms.Control.Dock%2A> Propriedade como. <xref:System.Windows.Forms.DockStyle.Fill>

   O controle `elementHost2` será redimensionado para preencher a célula.

6. Selecione o controle <xref:System.Windows.Forms.TableLayoutPanel>.

7. Defina o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Top>.

8. Selecione `elementHost3`.

9. Defina o valor de sua <xref:System.Windows.Forms.Control.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Fill>.

   O controle `elementHost3` será redimensionado para preencher o espaço restante no formulário.

10. Redimensione o formulário.

    Todos os <xref:System.Windows.Forms.Integration.ElementHost> três controles são redimensionados adequadamente.

    Para obter mais informações, confira [Como: Ancorar e encaixar controles filho](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)em um controle TableLayoutPanel.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Como: Alinhar um controle às bordas dos formulários no tempo de design](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Passo a passo: Organizando controles em Windows Forms usando Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migração e interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)

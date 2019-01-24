---
title: 'Como: Definir plano de fundo de um painel dos Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: be0359e13bcab868374189c6b42df392327b8eb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645048"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Como: Definir plano de fundo de um painel dos Windows Forms usando o Designer
Um Windows Forms <xref:System.Windows.Forms.Panel> controle pode exibir uma cor de fundo e uma imagem de plano de fundo. O <xref:System.Windows.Forms.Control.BackColor%2A> propriedade define a cor de plano de fundo de controles que estão contidos no painel, como rótulos e botões de opção. Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> não está definida, o <xref:System.Windows.Forms.Control.BackColor%2A> seleção preencherá todos o painel. Se o <xref:System.Windows.Forms.Control.BackgroundImage%2A> estiver definida, a imagem será exibida por trás dos controles que estão contidos no painel.  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contenha um <xref:System.Windows.Forms.Panel> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [como: Adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Para definir a tela de fundo no Designer de Formulários do Windows  
  
1.  Selecione o <xref:System.Windows.Forms.Panel> controle.  
  
2.  No **propriedades** , clique na seta ao lado de <xref:System.Windows.Forms.Control.BackColor%2A> propriedade para exibir uma janela com três guias.  
  
3.  Selecione a guia **Personalizado** para exibir uma paleta de cores.  
  
4.  Selecione a guia **Web** ou **Sistema** para exibir uma lista de nomes predefinidos para cores e, em seguida, selecione uma cor.  
  
5.  No **propriedades** , clique na seta ao lado de <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade.  
  
6.  Na caixa de diálogo **Abrir**, selecione o arquivo que deseja exibir.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Controle de painel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [Visão geral do controle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [Como: Agrupar controles com o controle de painel do Windows Forms usando o Designer](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)

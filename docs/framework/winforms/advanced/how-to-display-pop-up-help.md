---
title: 'Como: Exibir Ajuda pop-up'
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: e017e25f140d3dfd260545f28fab73905fe149fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601838"
---
# <a name="how-to-display-pop-up-help"></a>Como: Exibir Ajuda pop-up
Uma maneira de exibir a Ajuda no Windows Forms é por meio de **ajuda** botão, localizado no lado direito da barra de título, acessível por meio o <xref:System.Windows.Forms.Form.HelpButton%2A> propriedade. Esse tipo de exibição de Ajuda é adequado para uso com caixas de diálogo. Caixas de diálogo mostradas modalmente (com o <xref:System.Windows.Forms.Form.ShowDialog%2A> método) enfrentam dificuldades ajuda externa sistemas, como caixas de diálogo modais precisam ser fechadas antes que o foco pode alternar para outra janela. Além disso, usar o botão **Ajuda** requer que não nenhum botão **Minimizar** ou **Maximizar** seja mostrado na barra de título. Isso é uma convenção padrão de caixas de diálogo, enquanto formulários geralmente têm os botões **Minimizar** e **Maximizar**.  
  
 Lembre-se de que você também pode usar o <xref:System.Windows.Forms.HelpProvider> componente para vincular controles a arquivos em um sistema de Ajuda, mesmo se você tiver implementado Ajuda pop-up. Para obter mais informações, consulte [Fornecer ajuda em um aplicativo do Windows](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-display-pop-up-help"></a>Exibir a Ajuda pop-up  
  
1.  Arraste um componente [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) da Caixa de ferramentas para seu formulário.  
  
     Ele ficará na bandeja na parte inferior do Designer de Formulários do Windows.  
  
2.  Na janela Propriedades, defina as <xref:System.Windows.Forms.Form.HelpButton%2A> propriedade para `true`. Isso exibirá um botão com um ponto de interrogação no lado direito da barra de título do formulário.  
  
3.  Para que o <xref:System.Windows.Forms.Form.HelpButton%2A> para exibir o formulário <xref:System.Windows.Forms.Form.MinimizeBox%2A> e <xref:System.Windows.Forms.Form.MaximizeBox%2A> propriedades devem ser definidas como `false`, o <xref:System.Windows.Forms.Form.ControlBox%2A> propriedade definida como `true`e o <xref:System.Windows.Forms.Form.FormBorderStyle%2A> propriedade para um dos seguintes valores: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> ou <xref:System.Windows.Forms.FormBorderStyle.Sizable>.  
  
4.  Selecione o controle para o qual você deseja exibir a Ajuda no seu formulário e defina a cadeia de caracteres de Ajuda na janela Propriedades. Esta é a cadeia de texto que será exibida em uma janela similar a uma [ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).  
  
5.  Pressione **F5**.  
  
6.  Pressione o botão **Ajuda** na barra de título e clique no controle no qual você definiu a cadeia de caracteres de Ajuda.  
  
## <a name="see-also"></a>Consulte também
- [Ajuda de Controle Usando ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)
- [Integrando a Ajuda do Usuário nos Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)
- [Windows Forms](../../../../docs/framework/winforms/index.md)

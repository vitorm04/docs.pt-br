---
title: Como alinhar um controle às bordas de formulários na hora do design
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: 5b36879413442ff99da034fcbee6bf6388affa6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>Como alinhar um controle às bordas de formulários na hora do design
Você pode fazer com que o seu controle alinhe a borda de formulários, definindo o <xref:System.Windows.Forms.Control.Dock%2A>. Essa propriedade determina onde reside o controle no formulário. O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:  
  
|Configuração|Efeito no seu controle|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|Encaixa na parte inferior do formulário.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Preenche todo o espaço restante no formulário.|  
|<xref:System.Windows.Forms.DockStyle.Left>|Encaixa do lado esquerdo do formulário.|  
|<xref:System.Windows.Forms.DockStyle.None>|Faz não encaixe em qualquer local e ele aparece no local especificado por seu <xref:System.Windows.Forms.Control.Location%2A>.|  
|<xref:System.Windows.Forms.DockStyle.Right>|Encaixa do lado direito do formulário.|  
|<xref:System.Windows.Forms.DockStyle.Top>|Encaixa na parte superior do formulário.|  
  
 Esses valores também podem ser definidos no código. Para obter mais informações, consulte [Como alinhar um controle às bordas de formulários](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a>Para definir a propriedade Dock para o seu controle no tempo de design  
  
1.  No Designer de Formulários do Windows, selecione seu controle.  
  
2.  No **propriedades** janela, clique na lista suspensa ao lado de caixa de <xref:System.Windows.Forms.Control.Dock%2A> propriedade.  
  
     Uma interface gráfica que representa os possíveis seis <xref:System.Windows.Forms.Control.Dock%2A> configurações é exibida.  
  
3.  Escolha a configuração apropriada.  
  
4.  O controle agora será encaixado da maneira especificada pela configuração.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [Como alinhar um controle às bordas de formulários](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Como ancorar controles no Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Como ancorar e encaixar controles filho em um controle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Como ancorar e encaixar controles filho em um controle FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Desenvolvendo controles dos Windows Forms em tempo de design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)

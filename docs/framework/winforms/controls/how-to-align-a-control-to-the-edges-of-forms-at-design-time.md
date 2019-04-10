---
title: 'Como: Alinhar um controle às bordas de formulários no tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: 8ca6fd64edbd73301fd298f42c3d4d97d021888a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331852"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>Como: Alinhar um controle às bordas de formulários no tempo de design
Você pode fazer com que o seu controle Alinhar à borda de seus formulários configurando o <xref:System.Windows.Forms.Control.Dock%2A>. Essa propriedade determina onde reside o controle no formulário. O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:  
  
|Configuração|Efeito no seu controle|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|Encaixa na parte inferior do formulário.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Preenche todo o espaço restante no formulário.|  
|<xref:System.Windows.Forms.DockStyle.Left>|Encaixa do lado esquerdo do formulário.|  
|<xref:System.Windows.Forms.DockStyle.None>|Não se encaixa em qualquer lugar e aparece no local especificado pelo seu <xref:System.Windows.Forms.Control.Location%2A>.|  
|<xref:System.Windows.Forms.DockStyle.Right>|Encaixa do lado direito do formulário.|  
|<xref:System.Windows.Forms.DockStyle.Top>|Encaixa na parte superior do formulário.|  
  
 Esses valores também podem ser definidos no código. Para obter mais informações, confira [Como: Alinhar um controle às bordas de formulários](how-to-align-a-control-to-the-edges-of-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a>Para definir a propriedade Dock para o seu controle no tempo de design  
  
1. No Designer de Formulários do Windows, selecione seu controle.  
  
2. No **propriedades** , clique na lista suspensa caixa ao lado de <xref:System.Windows.Forms.Control.Dock%2A> propriedade.  
  
     Uma interface gráfica que representa os seis possíveis <xref:System.Windows.Forms.Control.Dock%2A> configurações é exibida.  
  
3. Escolha a configuração apropriada.  
  
4. O controle agora será encaixado da maneira especificada pela configuração.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Como: Alinhar um controle às bordas de formulários](how-to-align-a-control-to-the-edges-of-forms.md)
- [Passo a passo: Organizar controles nos Windows Forms usando linhas de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Como: Ancorar controles nos Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Passo a passo: Organizar controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Desenvolvendo controles dos Windows Forms na hora de design](developing-windows-forms-controls-at-design-time.md)

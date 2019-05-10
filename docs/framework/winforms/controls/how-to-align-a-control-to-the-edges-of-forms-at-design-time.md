---
title: 'Como: Alinhar um controle às bordas de formulários no tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b08e01eb9adb984a32a8fc435cf1f3b93b159a14
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210375"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>Como: Alinhar um controle às bordas de formulários no tempo de design

Você pode fazer com que o seu controle Alinhar à borda de seus formulários, definindo o valor da <xref:System.Windows.Forms.Control.Dock%2A> propriedade. Essa propriedade determina onde reside o controle no formulário. O <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:

|Configuração|Efeito no seu controle|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|Encaixa na parte inferior do formulário.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Preenche todo o espaço restante no formulário.|
|<xref:System.Windows.Forms.DockStyle.Left>|Encaixa do lado esquerdo do formulário.|
|<xref:System.Windows.Forms.DockStyle.None>|Não se encaixa em qualquer lugar e aparece no local especificado pelo seu <xref:System.Windows.Forms.Control.Location%2A>.|
|<xref:System.Windows.Forms.DockStyle.Right>|Encaixa do lado direito do formulário.|
|<xref:System.Windows.Forms.DockStyle.Top>|Encaixa na parte superior do formulário.|

Esses valores também podem ser definidos no código. Para obter mais informações, confira [Como: Alinhar um controle às bordas de formulários](how-to-align-a-control-to-the-edges-of-forms.md).

## <a name="set-the-dock-property-for-your-control-at-design-time"></a>Defina a propriedade Dock para o seu controle em tempo de design

1. No Designer de formulários do Windows no Visual Studio, selecione seu controle.

2. No **propriedades** , clique na lista suspensa caixa ao lado de <xref:System.Windows.Forms.Control.Dock%2A> propriedade.

     Uma interface gráfica que representa os seis possíveis <xref:System.Windows.Forms.Control.Dock%2A> configurações é exibida.

3. Escolha a configuração apropriada.

4. O controle agora será encaixado da maneira especificada pela configuração.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Como: Alinhar um controle às bordas de formulários](how-to-align-a-control-to-the-edges-of-forms.md)
- [Passo a passo: Organizando controles nos formulários do Windows usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Como: Ancoragem de controles nos Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)

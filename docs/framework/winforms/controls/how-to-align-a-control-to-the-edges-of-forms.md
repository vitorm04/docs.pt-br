---
title: 'Como: Alinhar um controle às bordas de formulários'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015942"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Como: Alinhar um controle às bordas de formulários

Você pode fazer com que seu controle fique alinhado à borda de seus formulários <xref:System.Windows.Forms.Control.Dock%2A> definindo a propriedade. Essa propriedade determina onde reside o controle no formulário. A <xref:System.Windows.Forms.Control.Dock%2A> propriedade pode ser definida com os seguintes valores:

|Configuração|Efeito no seu controle|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|Encaixa na parte inferior do formulário.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Preenche todo o espaço restante no formulário.|
|<xref:System.Windows.Forms.DockStyle.Left>|Encaixa do lado esquerdo do formulário.|
|<xref:System.Windows.Forms.DockStyle.None>|Não encaixa em nenhum lugar e aparece no local especificado por sua <xref:System.Windows.Forms.Control.Location%2A> propriedade.|
|<xref:System.Windows.Forms.DockStyle.Right>|Encaixa do lado direito do formulário.|
|<xref:System.Windows.Forms.DockStyle.Top>|Encaixa na parte superior do formulário.|

Há suporte para o tempo de design para esse recurso no Visual Studio.

## <a name="set-the-dock-property-for-your-control-at-run-time"></a>Definir a propriedade Dock para seu controle em tempo de execução

Defina a <xref:System.Windows.Forms.Control.Dock%2A> propriedade para o valor apropriado no código.

```vb
' To set the Dock property internally.
Me.Dock = DockStyle.Top
' To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top
```

```csharp
// To set the Dock property internally.
this.Dock = DockStyle.Top;
// To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top;
```

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)
- [Como: Ancorar e encaixar controles filho em um controle FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Como: Ancorar e encaixar controles filho em um controle TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)

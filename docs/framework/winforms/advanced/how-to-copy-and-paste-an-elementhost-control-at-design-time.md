---
title: Como copiar e colar um controle ElementHost em tempo de design
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e89510558274558e560bf810afe746e250ff26a4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459223"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Como copiar e colar um controle ElementHost

Este procedimento mostra como copiar um controle Windows Presentation Foundation (WPF) em um formulário do Windows no Visual Studio.

1. No Visual Studio, adicione um novo <xref:System.Windows.Controls.UserControl> do WPF a um projeto Windows Forms. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. Na janela **Propriedades** , defina o valor do <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades de `UserControl1` como **200**.

3. Defina o valor da propriedade <xref:System.Windows.Controls.Control.Background%2A> como **azul**.

4. Compile o projeto.

5. Abra `Form1` no Designer de Formulários do Windows.

6. Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.

   Uma instância de `UserControl1` é hospedada em um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost1`.

7. Com `elementHost1` selecionado, pressione **Ctrl**+**C** para copiá-lo para a área de transferência.

8. Pressione **Ctrl**+**V** para colar o controle copiado no formulário.

   Um novo controle de <xref:System.Windows.Forms.Integration.ElementHost> chamado `elementHost2` é criado no formulário.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migração e Interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)

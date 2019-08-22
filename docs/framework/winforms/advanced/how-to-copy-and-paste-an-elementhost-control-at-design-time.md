---
title: 'Como: copiar e colar um controle ElementHost em tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666174"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Como: Copiar e colar um controle ElementHost

Este procedimento mostra como copiar um controle Windows Presentation Foundation (WPF) em um formulário do Windows no Visual Studio.

1. No Visual Studio, adicione um novo WPF <xref:System.Windows.Controls.UserControl> a um projeto Windows Forms. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, confira [Passo a passo: Criando novo conteúdo do WPF em Windows Forms em tempo](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de design.

2. Na janela **Propriedades** , defina o <xref:System.Windows.FrameworkElement.Width%2A> valor das propriedades e <xref:System.Windows.FrameworkElement.Height%2A> de `UserControl1` como **200**.

3. Defina o valor da <xref:System.Windows.Controls.Control.Background%2A> Propriedade como **azul**.

4. Compile o projeto.

5. Abra `Form1` no Designer de Formulários do Windows.

6. Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.

   Uma instância do `UserControl1` é hospedada em um <xref:System.Windows.Forms.Integration.ElementHost> novo controle `elementHost1`chamado.

7. Com `elementHost1` selecionado, pressione **Ctrl**+**C** para copiá-lo para a área de transferência.

8. Pressione **Ctrl**+**V** para colar o controle copiado no formulário.

   Um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost2` é criado no formulário.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migração e interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)
- [Usando Controles do WPF](using-wpf-controls.md)
- [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)

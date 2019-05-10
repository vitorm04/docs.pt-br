---
title: Usando controles WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 149a2da1303e6b801a439494254a416a38b145a7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211306"
---
# <a name="use-wpf-controls"></a>Usar controles WPF

Você pode usar controles do WPF (Windows Presentation Foundation) em seus aplicativos do Windows Forms. Embora essas sejam duas tecnologias de exibição diferentes, elas interoperam com harmonia.

O Designer de formulários do Windows no Visual Studio fornece um ambiente de design visual para hospedar controles do Windows Presentation Foundation. Um controle WPF é hospedado por um controle Windows Forms especial chamado <xref:System.Windows.Forms.Integration.ElementHost>. Esse controle permite que o controle WPF participe do layout do formulário e receba mensagens de teclado e mouse. Em tempo de design, você pode organizar o <xref:System.Windows.Forms.Integration.ElementHost> controlar exatamente como faria com qualquer controle dos Windows Forms.

Você também pode usar controles do Windows Forms em seus aplicativos do WPF. Para obter mais informações, consulte [Design XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).

## <a name="in-this-section"></a>Nesta seção

[Como: Copiar e colar um controle ElementHost em tempo de Design](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)\
Mostra como copiar um controle Windows Presentation Foundation em um Windows Form.

[Passo a passo: Organizando conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)\
Mostra como usar os recursos de layout do Windows Forms, como ancoragem e guias de alinhamento para organizar controles do Windows Presentation Foundation.

[Passo a passo: Criando novo conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)\
Mostra como criar um controle do Windows Presentation Foundation para uso em aplicativos do Windows Forms.

[Passo a passo: Atribuindo conteúdo WPF nos Windows Forms em tempo de Design](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)\
Mostra como selecionar os tipos de controle do Windows Presentation Foundation que você deseja exibir em seu formulário.

[Passo a passo: Criando o conteúdo WPF](walkthrough-styling-wpf-content.md)\
Mostra o fluxo de trabalho entre o Designer de Formulários do Windows e o [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] para aplicar estilos aos controles do Windows Presentation Foundation.

## <a name="reference"></a>Referência

<xref:System.Windows.Forms.Integration.ElementHost>\
Descreve uma classe que você pode usar para hospedar os controles do Windows Presentation Foundation em seus aplicativos do Windows Forms.

<xref:System.Windows.Forms.Integration.WindowsFormsHost>\
Descreve uma classe que você pode usar para hospedar controles do Windows Forms no seu aplicativo do Windows Presentation Foundation.

## <a name="related-sections"></a>Seções relacionadas

[Migração e Interoperabilidade](../../wpf/advanced/migration-and-interoperability.md)\
Descreve a interoperação entre as tecnologias Windows Presentation Foundation e Windows Forms.

[Design XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)\
Descreve como criar controles de Windows Presentation Foundation no Visual Studio.

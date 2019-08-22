---
title: Usando controles WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5ea92b24a2ca30c0ad137d83c8f521a952ad0c6b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658494"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Usar controles WPF em aplicativos Windows Forms

Você pode usar controles Windows Presentation Foundation (WPF) em aplicativos baseados em Windows Forms. Embora essas sejam duas tecnologias de exibição diferentes, elas interoperam com harmonia.

O Designer de Formulários do Windows no Visual Studio fornece um ambiente de Design Visual para hospedar Windows Presentation Foundation controles. Um controle WPF é hospedado por um controle de Windows Forms especial chamado <xref:System.Windows.Forms.Integration.ElementHost>. Esse controle permite que o controle WPF participe do layout do formulário e receba mensagens de teclado e mouse. Em tempo de design, você pode organizar <xref:System.Windows.Forms.Integration.ElementHost> o controle da mesma forma que faria com qualquer controle de Windows Forms.

Você também pode usar controles de Windows Forms em aplicativos baseados em WPF. Para obter mais informações, consulte [criar XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Consulte também

- [Interoperação do WPF e Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

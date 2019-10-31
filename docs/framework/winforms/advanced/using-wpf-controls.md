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
ms.openlocfilehash: 5e05ec7fc503565333a4d05662a4e40d8d1193af
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197469"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Usar controles WPF em aplicativos Windows Forms

Você pode usar controles Windows Presentation Foundation (WPF) em aplicativos baseados em Windows Forms. Embora essas sejam duas tecnologias de exibição diferentes, elas interoperam com harmonia.

O Designer de Formulários do Windows no Visual Studio fornece um ambiente de Design Visual para hospedar Windows Presentation Foundation controles. Um controle WPF é hospedado por um controle de Windows Forms especial chamado <xref:System.Windows.Forms.Integration.ElementHost>. Esse controle permite que o controle WPF participe do layout do formulário e receba mensagens de teclado e mouse. Em tempo de design, você pode organizar o controle de <xref:System.Windows.Forms.Integration.ElementHost> da mesma forma que faria com qualquer controle de Windows Forms.

Você também pode usar controles de Windows Forms em aplicativos baseados em WPF. Para obter mais informações, consulte [criar XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Consulte também

- [Interoperação do WPF e Windows Forms](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)

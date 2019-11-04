---
title: Usando controles WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9883e9d31fc9e3e2ec3ca06b4fc830bcdc338ae
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460700"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="1a2e8-102">Usar controles WPF em aplicativos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a2e8-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="1a2e8-103">Você pode usar controles Windows Presentation Foundation (WPF) em aplicativos baseados em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1a2e8-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="1a2e8-104">Embora essas sejam duas tecnologias de exibição diferentes, elas interoperam com harmonia.</span><span class="sxs-lookup"><span data-stu-id="1a2e8-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="1a2e8-105">O Designer de Formulários do Windows no Visual Studio fornece um ambiente de Design Visual para hospedar Windows Presentation Foundation controles.</span><span class="sxs-lookup"><span data-stu-id="1a2e8-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="1a2e8-106">Um controle WPF é hospedado por um controle de Windows Forms especial chamado <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="1a2e8-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="1a2e8-107">Esse controle permite que o controle WPF participe do layout do formulário e receba mensagens de teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="1a2e8-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="1a2e8-108">Em tempo de design, você pode organizar o controle de <xref:System.Windows.Forms.Integration.ElementHost> da mesma forma que faria com qualquer controle de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1a2e8-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="1a2e8-109">Você também pode usar controles de Windows Forms em aplicativos baseados em WPF.</span><span class="sxs-lookup"><span data-stu-id="1a2e8-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="1a2e8-110">Para obter mais informações, consulte [criar XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1a2e8-110">For more information, see [Design XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a2e8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a2e8-111">See also</span></span>

- [<span data-ttu-id="1a2e8-112">Interoperação do WPF e Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a2e8-112">WPF and Windows Forms interoperation</span></span>](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)

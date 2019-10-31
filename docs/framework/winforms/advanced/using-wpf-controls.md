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
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="1373e-102">Usar controles WPF em aplicativos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1373e-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="1373e-103">Você pode usar controles Windows Presentation Foundation (WPF) em aplicativos baseados em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1373e-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="1373e-104">Embora essas sejam duas tecnologias de exibição diferentes, elas interoperam com harmonia.</span><span class="sxs-lookup"><span data-stu-id="1373e-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="1373e-105">O Designer de Formulários do Windows no Visual Studio fornece um ambiente de Design Visual para hospedar Windows Presentation Foundation controles.</span><span class="sxs-lookup"><span data-stu-id="1373e-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="1373e-106">Um controle WPF é hospedado por um controle de Windows Forms especial chamado <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="1373e-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="1373e-107">Esse controle permite que o controle WPF participe do layout do formulário e receba mensagens de teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="1373e-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="1373e-108">Em tempo de design, você pode organizar o controle de <xref:System.Windows.Forms.Integration.ElementHost> da mesma forma que faria com qualquer controle de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1373e-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="1373e-109">Você também pode usar controles de Windows Forms em aplicativos baseados em WPF.</span><span class="sxs-lookup"><span data-stu-id="1373e-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="1373e-110">Para obter mais informações, consulte [criar XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1373e-110">For more information, see [Design XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="1373e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1373e-111">See also</span></span>

- [<span data-ttu-id="1373e-112">Interoperação do WPF e Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1373e-112">WPF and Windows Forms interoperation</span></span>](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)

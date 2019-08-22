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
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="e42b5-102">Usar controles WPF em aplicativos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e42b5-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="e42b5-103">Você pode usar controles Windows Presentation Foundation (WPF) em aplicativos baseados em Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e42b5-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="e42b5-104">Embora essas sejam duas tecnologias de exibição diferentes, elas interoperam com harmonia.</span><span class="sxs-lookup"><span data-stu-id="e42b5-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="e42b5-105">O Designer de Formulários do Windows no Visual Studio fornece um ambiente de Design Visual para hospedar Windows Presentation Foundation controles.</span><span class="sxs-lookup"><span data-stu-id="e42b5-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="e42b5-106">Um controle WPF é hospedado por um controle de Windows Forms especial chamado <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="e42b5-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="e42b5-107">Esse controle permite que o controle WPF participe do layout do formulário e receba mensagens de teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="e42b5-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="e42b5-108">Em tempo de design, você pode organizar <xref:System.Windows.Forms.Integration.ElementHost> o controle da mesma forma que faria com qualquer controle de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e42b5-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="e42b5-109">Você também pode usar controles de Windows Forms em aplicativos baseados em WPF.</span><span class="sxs-lookup"><span data-stu-id="e42b5-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="e42b5-110">Para obter mais informações, consulte [criar XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e42b5-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="e42b5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e42b5-111">See also</span></span>

- [<span data-ttu-id="e42b5-112">Interoperação do WPF e Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e42b5-112">WPF and Windows Forms interoperation</span></span>](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

---
title: 'Como: Detectar se o plug-in do WPF para Firefox está instalado'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: f84a0a2af43931b3ada1f674390ec5d841b79a1c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690426"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="bf8f3-102">Como: Detectar se o plug-in do WPF para Firefox está instalado</span><span class="sxs-lookup"><span data-stu-id="bf8f3-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>

<span data-ttu-id="bf8f3-103">O Windows Presentation Foundation (WPF) plug-in para Firefox habilita [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] e perder arquivos XAML para ser executado no navegador Mozilla Firefox.</span><span class="sxs-lookup"><span data-stu-id="bf8f3-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="bf8f3-104">Este tópico fornece um script escrito em HTML e JavaScript que os administradores podem usar para determinar se o WPF plug-in para Firefox está instalado.</span><span class="sxs-lookup"><span data-stu-id="bf8f3-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>

> [!NOTE]
> <span data-ttu-id="bf8f3-105">Para obter mais informações sobre como instalar, implantar e detectar o .NET Framework, consulte [instalar o .NET Framework para desenvolvedores](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="bf8f3-105">For more information about installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>

## <a name="example"></a><span data-ttu-id="bf8f3-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf8f3-106">Example</span></span>

<span data-ttu-id="bf8f3-107">Quando o .NET Framework 3.5 está instalado, o computador cliente é configurado com um plug-in do WPF para Firefox.</span><span class="sxs-lookup"><span data-stu-id="bf8f3-107">When the .NET Framework 3.5 is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="bf8f3-108">O script de exemplo a seguir verifica o plug-in do WPF para Firefox e, em seguida, exibe uma mensagem de status apropriado.</span><span class="sxs-lookup"><span data-stu-id="bf8f3-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>

```html
<HTML>

  <HEAD>
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />
    <SCRIPT type="text/javascript">
    <!--
    function OnLoad()
    {

       // Check for the WPF plug-in for Firefox and report
       var msg = "The WPF plug-in for Firefox is ";
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];
       if( wpfPlugin != null ) {
          document.writeln(msg + " installed.");
       }
       else {
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");
       }
    }
    -->
    </SCRIPT>
  </HEAD>

  <BODY onload="OnLoad()" />

</HTML>
```

<span data-ttu-id="bf8f3-109">Se a verificação para o plug-in do WPF para Firefox for bem-sucedida, a seguinte mensagem de status é exibida:</span><span class="sxs-lookup"><span data-stu-id="bf8f3-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is installed.`

<span data-ttu-id="bf8f3-110">Caso contrário, a seguinte mensagem de status é exibida:</span><span class="sxs-lookup"><span data-stu-id="bf8f3-110">Otherwise, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a><span data-ttu-id="bf8f3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf8f3-111">See also</span></span>

- [<span data-ttu-id="bf8f3-112">Detectar se o .NET Framework 3.0 está instalado</span><span class="sxs-lookup"><span data-stu-id="bf8f3-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="bf8f3-113">Detectar se o .NET Framework 3.5 está instalado</span><span class="sxs-lookup"><span data-stu-id="bf8f3-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="bf8f3-114">Visão geral dos aplicativos de navegador XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="bf8f3-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)

---
title: "Como detectar se o plug-in do WPF para Firefox está instalado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e821bd95679372fd169b7880e969fd10b5d03c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="a7d20-102">Como detectar se o plug-in do WPF para Firefox está instalado</span><span class="sxs-lookup"><span data-stu-id="a7d20-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>
<span data-ttu-id="a7d20-103">O [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] plug-in permite que o Firefox [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] e perder arquivos XAML para ser executado no navegador Mozilla Firefox.</span><span class="sxs-lookup"><span data-stu-id="a7d20-103">The [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] plug-in for Firefox enables [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="a7d20-104">Este tópico fornece um script escrito em HTML e JavaScript que os administradores podem usar para determinar se o plug-in para o Firefox do WPF está instalado.</span><span class="sxs-lookup"><span data-stu-id="a7d20-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7d20-105">Para obter mais informações sobre como instalar, implantar e detectar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], consulte [instalar o .NET Framework para desenvolvedores](../../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="a7d20-105">For more information about installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7d20-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7d20-106">Example</span></span>  
 <span data-ttu-id="a7d20-107">Quando o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] é instalado, o computador cliente é configurado com um plug-in do WPF para o Firefox.</span><span class="sxs-lookup"><span data-stu-id="a7d20-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="a7d20-108">O script de exemplo a seguir verifica o plug-in do WPF para Firefox e, em seguida, exibe uma mensagem de status apropriado.</span><span class="sxs-lookup"><span data-stu-id="a7d20-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>  
  
```  
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
  
 <span data-ttu-id="a7d20-109">Se a verificação de WPF plug-in para o Firefox for bem-sucedida, a seguinte mensagem de status será exibida:</span><span class="sxs-lookup"><span data-stu-id="a7d20-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is installed.`  
  
 <span data-ttu-id="a7d20-110">Caso contrário, a seguinte mensagem de status é exibida:</span><span class="sxs-lookup"><span data-stu-id="a7d20-110">Otherwise, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a><span data-ttu-id="a7d20-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7d20-111">See Also</span></span>  
 [<span data-ttu-id="a7d20-112">Detectar se o .NET Framework 3.0 está instalado</span><span class="sxs-lookup"><span data-stu-id="a7d20-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [<span data-ttu-id="a7d20-113">Detectar se o .NET Framework 3.5 está instalado</span><span class="sxs-lookup"><span data-stu-id="a7d20-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [<span data-ttu-id="a7d20-114">Visão geral dos aplicativos de navegador XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="a7d20-114">WPF XAML Browser Applications Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)

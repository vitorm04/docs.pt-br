---
title: Como detectar se o plug-in do WPF para Firefox está instalado
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: ba411d662a8e5b0c4727e23c8d507e8924b6e9e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546982"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Como detectar se o plug-in do WPF para Firefox está instalado
Permite que o Windows Presentation Foundation (WPF) plug-in para o Firefox [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] e perder arquivos XAML para ser executado no navegador Mozilla Firefox. Este tópico fornece um script escrito em HTML e JavaScript que os administradores podem usar para determinar se o plug-in para o Firefox do WPF está instalado.  
  
> [!NOTE]
>  Para obter mais informações sobre como instalar, implantar e detectar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], consulte [instalar o .NET Framework para desenvolvedores](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Exemplo  
 Quando o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] é instalado, o computador cliente é configurado com um plug-in do WPF para o Firefox. O script de exemplo a seguir verifica o plug-in do WPF para Firefox e, em seguida, exibe uma mensagem de status apropriado.  
  
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
  
 Se a verificação de WPF plug-in para o Firefox for bem-sucedida, a seguinte mensagem de status será exibida:  
  
 `The WPF plug-in for Firefox is installed.`  
  
 Caso contrário, a seguinte mensagem de status é exibida:  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>Consulte também  
 [Detectar se o .NET Framework 3.0 está instalado](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [Detectar se o .NET Framework 3.5 está instalado](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [Visão geral dos aplicativos de navegador XAML do WPF](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)

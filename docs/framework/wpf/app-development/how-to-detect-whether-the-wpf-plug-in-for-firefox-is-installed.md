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
ms.openlocfilehash: 3cc2f95627bc35fa4cb6c486d3b8ad61f69d7fea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372874"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Como: Detectar se o plug-in do WPF para Firefox está instalado
O Windows Presentation Foundation (WPF) plug-in para Firefox habilita [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] e perder arquivos XAML para ser executado no navegador Mozilla Firefox. Este tópico fornece um script escrito em HTML e JavaScript que os administradores podem usar para determinar se o WPF plug-in para Firefox está instalado.  
  
> [!NOTE]
>  Para obter mais informações sobre como instalar, implantar e detectar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], consulte [instalar o .NET Framework para desenvolvedores](../../install/guide-for-developers.md).  
  
## <a name="example"></a>Exemplo  
 Quando o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] é instalado, o computador cliente é configurado com um plug-in do WPF para Firefox. O script de exemplo a seguir verifica o plug-in do WPF para Firefox e, em seguida, exibe uma mensagem de status apropriado.  
  
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
  
 Se a verificação para o plug-in do WPF para Firefox for bem-sucedida, a seguinte mensagem de status é exibida:  
  
 `The WPF plug-in for Firefox is installed.`  
  
 Caso contrário, a seguinte mensagem de status é exibida:  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>Consulte também
- [Detectar se o .NET Framework 3.0 está instalado](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [Detectar se o .NET Framework 3.5 está instalado](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [Visão geral dos aplicativos de navegador XAML do WPF](wpf-xaml-browser-applications-overview.md)

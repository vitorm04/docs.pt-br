---
title: Detectar se o plug-in do WPF para Firefox está instalado
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 91680859c1742e5d5443d626c81273a80504f4a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740403"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Como detectar se o plug-in do WPF para Firefox está instalado

O plug-in Windows Presentation Foundation (WPF) para Firefox permite que os aplicativos de navegador XAML (XBAPs) e arquivos XAML soltos sejam executados no navegador Mozilla Firefox. Este tópico fornece um script escrito em HTML e JavaScript que os administradores podem usar para determinar se o plug-in do WPF para o Firefox está instalado.

> [!NOTE]
> Para obter mais informações sobre como instalar, implantar e detectar o .NET Framework, consulte [instalar o .NET Framework para desenvolvedores](../../install/guide-for-developers.md).

## <a name="example"></a>{1&gt;Exemplo&lt;1}

Quando o .NET Framework 3,5 é instalado, o computador cliente é configurado com um plug-in do WPF para o Firefox. O script de exemplo a seguir verifica o plug-in do WPF para Firefox e, em seguida, exibe uma mensagem de status apropriada.

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

Se a verificação do plug-in do WPF para o Firefox for bem-sucedida, a seguinte mensagem de status será exibida:

`The WPF plug-in for Firefox is installed.`

Caso contrário, a seguinte mensagem de status será exibida:

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>Consulte também

- [Detectar se o .NET Framework 3.0 está instalado](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [Detectar se o .NET Framework 3.5 está instalado](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [Visão geral dos aplicativos de navegador XAML do WPF](wpf-xaml-browser-applications-overview.md)

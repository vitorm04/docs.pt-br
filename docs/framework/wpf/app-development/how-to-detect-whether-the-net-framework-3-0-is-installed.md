---
title: Como detectar se o .NET Framework 3.0 está instalado
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 09de427980ecfb515b8d341d0d7833b878140286
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546485"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="afdab-102">Como detectar se o .NET Framework 3.0 está instalado</span><span class="sxs-lookup"><span data-stu-id="afdab-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="afdab-103">Antes dos administradores podem implantar aplicativos do Microsoft .NET Framework em um sistema, eles devem primeiro confirmar que o tempo de execução do .NET Framework está presente.</span><span class="sxs-lookup"><span data-stu-id="afdab-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="afdab-104">Este tópico fornece um script escrito em HTML/JavaScript que os administradores podem usar para determinar se o .NET Framework está presente em um sistema.</span><span class="sxs-lookup"><span data-stu-id="afdab-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afdab-105">Para obter mais informações sobre como instalar, implantar e detectar o Microsoft .NET Framework, consulte a discussão na [Implantando o Microsoft .NET Framework versão 3.0](http://go.microsoft.com/fwlink/?LinkId=96739).</span><span class="sxs-lookup"><span data-stu-id="afdab-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](http://go.microsoft.com/fwlink/?LinkId=96739).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="afdab-106">Detectar a cadeia de caracteres de agente de usuário ".NET CLR"</span><span class="sxs-lookup"><span data-stu-id="afdab-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="afdab-107">Quando o .NET Framework é instalado, o MSI adiciona ".NET CLR" e o número de versão para a cadeia de caracteres UserAgent.</span><span class="sxs-lookup"><span data-stu-id="afdab-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="afdab-108">O exemplo a seguir mostra um script inserido em uma página HTML simples.</span><span class="sxs-lookup"><span data-stu-id="afdab-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="afdab-109">O script procura a cadeia de caracteres UserAgent para determinar se o .NET Framework está instalado e exibe uma mensagem de status nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="afdab-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 <span data-ttu-id="afdab-110">Se a pesquisa pela versão ".NET CLR" for bem-sucedida, o seguinte tipo de mensagem de status será exibido:</span><span class="sxs-lookup"><span data-stu-id="afdab-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="afdab-111">Caso contrário, o seguinte tipo de mensagem de status será exibido:</span><span class="sxs-lookup"><span data-stu-id="afdab-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`

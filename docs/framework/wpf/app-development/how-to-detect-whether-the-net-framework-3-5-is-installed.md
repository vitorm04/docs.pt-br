---
title: 'Como: Detectar se o .NET Framework 3.5 está instalado'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: af2428ece79803953b8c90431d905824dd18fec8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947856"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a><span data-ttu-id="6bbbb-102">Como: Detectar se o .NET Framework 3.5 está instalado</span><span class="sxs-lookup"><span data-stu-id="6bbbb-102">How to: Detect Whether the .NET Framework 3.5 Is Installed</span></span>
<span data-ttu-id="6bbbb-103">Antes dos administradores podem implantar aplicativos do Windows Presentation Foundation (WPF) em um sistema que tem como alvo o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], eles devem primeiro confirmar que o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] tempo de execução está presente.</span><span class="sxs-lookup"><span data-stu-id="6bbbb-103">Before administrators can deploy Windows Presentation Foundation (WPF) applications on a system that targets the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], they must first confirm that the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] runtime is present.</span></span> <span data-ttu-id="6bbbb-104">Este tópico fornece um script escrito em HTML/JavaScript que os administradores podem usar para determinar se o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] está presente em um sistema.</span><span class="sxs-lookup"><span data-stu-id="6bbbb-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bbbb-105">Para obter mais informações sobre como instalar, implantar e detectar o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], consulte [instalar o .NET Framework para desenvolvedores](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="6bbbb-105">For more detailed information on installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bbbb-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6bbbb-106">Example</span></span>  
 <span data-ttu-id="6bbbb-107">Quando o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] é instalado, o MSI adiciona ".NET CLR" e o número de versão a cadeia de caracteres UserAgent.</span><span class="sxs-lookup"><span data-stu-id="6bbbb-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="6bbbb-108">O exemplo a seguir mostra um script inserido em uma página HTML simples.</span><span class="sxs-lookup"><span data-stu-id="6bbbb-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="6bbbb-109">O script procura a cadeia de caracteres UserAgent para determinar se o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] está instalado e exibe uma mensagem de status nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="6bbbb-109">The script searches the UserAgent string to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bbbb-110">Este script foi desenvolvido para o Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6bbbb-110">This script is designed for Internet Explorer.</span></span> <span data-ttu-id="6bbbb-111">Outros navegadores podem não incluir informações de CLR do .NET na cadeia de caracteres UserAgent.</span><span class="sxs-lookup"><span data-stu-id="6bbbb-111">Other browsers may not include .NET CLR information in the UserAgent string.</span></span>  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
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
  
 <span data-ttu-id="6bbbb-112">Se a pesquisa pela versão ".NET CLR" for bem-sucedida, o seguinte tipo de mensagem de status será exibido:</span><span class="sxs-lookup"><span data-stu-id="6bbbb-112">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 <span data-ttu-id="6bbbb-113">Caso contrário, o seguinte tipo de mensagem de status será exibido:</span><span class="sxs-lookup"><span data-stu-id="6bbbb-113">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a><span data-ttu-id="6bbbb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bbbb-114">See also</span></span>

- [<span data-ttu-id="6bbbb-115">Detectar se o .NET Framework 3.0 está instalado</span><span class="sxs-lookup"><span data-stu-id="6bbbb-115">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)

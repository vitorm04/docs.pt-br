---
title: Como configurar o Visual Studio para depurar um aplicativo de navegador XAML para chamar um serviço Web
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: 948a730185650cb3449202503a049e9caff7c4bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="0c91f-102">Como configurar o Visual Studio para depurar um aplicativo de navegador XAML para chamar um serviço Web</span><span class="sxs-lookup"><span data-stu-id="0c91f-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="0c91f-103"> executado em uma área restrita de segurança de confiança parcial que é restrita ao conjunto de permissões da zona da Internet.</span><span class="sxs-lookup"><span data-stu-id="0c91f-103"> run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="0c91f-104">Esse conjunto de permissões restringe as chamadas de serviço Web para apenas os serviços Web que estão localizados no site de origem do aplicativo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0c91f-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="0c91f-105">Quando um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] é depurado do [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], no entanto, ele não é considerado como tendo o mesmo site de origem que o serviço Web que ele referencia.</span><span class="sxs-lookup"><span data-stu-id="0c91f-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="0c91f-106">Isso faz com que exceções de segurança sejam geradas quando o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tenta chamar o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="0c91f-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="0c91f-107">No entanto, um projeto [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] pode ser configurado para simular o mesmo site de origem do serviço Web que ele chama durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="0c91f-107">However, a [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="0c91f-108">Isso permite que o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] chame com segurança o serviço Web sem causar exceções de segurança.</span><span class="sxs-lookup"><span data-stu-id="0c91f-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>  
  
## <a name="configuring-visual-studio"></a><span data-ttu-id="0c91f-109">Configurando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0c91f-109">Configuring Visual Studio</span></span>  
 <span data-ttu-id="0c91f-110">Para configurar [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] para depurar um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] que chama um serviço Web:</span><span class="sxs-lookup"><span data-stu-id="0c91f-110">To configure [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>  
  
1.  <span data-ttu-id="0c91f-111">Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0c91f-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0c91f-112">No **Designer de Projeto**, clique na guia **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="0c91f-112">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="0c91f-113">Na seção **Iniciar Ação**, selecione **Iniciar programa externo** e insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0c91f-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  <span data-ttu-id="0c91f-114">Na seção **Opções de inicialização**, digite o seguinte na caixa de texto **Argumentos da linha de comando**:</span><span class="sxs-lookup"><span data-stu-id="0c91f-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="0c91f-115">`-debug`  *nome de arquivo*</span><span class="sxs-lookup"><span data-stu-id="0c91f-115">`-debug`  *filename*</span></span>  
  
     <span data-ttu-id="0c91f-116">O valor *filename* para o parâmetro **-debug** é o nome do arquivo .xbap; por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0c91f-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  <span data-ttu-id="0c91f-117">Essa é a configuração padrão para soluções criadas com o modelo de projeto [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0c91f-117">This is the default configuration for solutions that are created with the [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>  
  
1.  <span data-ttu-id="0c91f-118">Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0c91f-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0c91f-119">No **Designer de Projeto**, clique na guia **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="0c91f-119">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="0c91f-120">Na seção **Opções de inicialização**, adicione o seguinte parâmetro de linha de comando para a caixa de texto **Argumentos de linha de comando**:</span><span class="sxs-lookup"><span data-stu-id="0c91f-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="0c91f-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="0c91f-121">`-debugSecurityZoneURL`  *URL*</span></span>  
  
     <span data-ttu-id="0c91f-122">O valor da *URL* para o parâmetro **-debugSecurityZoneURL** é o [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] para o local que você deseja simular como sendo o site de origem do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0c91f-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>  
  
 <span data-ttu-id="0c91f-123">Por exemplo, considere um [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] que usa um serviço Web com o seguinte [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="0c91f-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 <span data-ttu-id="0c91f-124">O site de origem [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] para esse serviço Web é:</span><span class="sxs-lookup"><span data-stu-id="0c91f-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>  
  
 `http://services.msdn.microsoft.com`  
  
 <span data-ttu-id="0c91f-125">Consequentemente, o parâmetro de linha de comando completo **-debugSecurityZoneURL** e seu valor é:</span><span class="sxs-lookup"><span data-stu-id="0c91f-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a><span data-ttu-id="0c91f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c91f-126">See Also</span></span>  
 [<span data-ttu-id="0c91f-127">Host do WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="0c91f-127">WPF Host (PresentationHost.exe)</span></span>](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)

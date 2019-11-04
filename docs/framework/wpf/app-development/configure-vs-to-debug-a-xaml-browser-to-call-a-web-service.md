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
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460908"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="899d5-102">Como configurar o Visual Studio para depurar um aplicativo de navegador XAML para chamar um serviço Web</span><span class="sxs-lookup"><span data-stu-id="899d5-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
<span data-ttu-id="899d5-103">Os aplicativos de navegador XAML (XBAPs) são executados em uma área de segurança de confiança parcial que é restrita ao conjunto de permissões de zona da Internet.</span><span class="sxs-lookup"><span data-stu-id="899d5-103">XAML browser applications (XBAPs) run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="899d5-104">Esse conjunto de permissões restringe as chamadas de serviço Web somente a serviços Web que estão localizados no site de origem do aplicativo XBAP.</span><span class="sxs-lookup"><span data-stu-id="899d5-104">This permission set restricts Web service calls to only Web services that are located at the XBAP application's site of origin.</span></span> <span data-ttu-id="899d5-105">No entanto, quando um XBAP é depurado do Visual Studio 2005, não é considerado ter o mesmo site de origem que o serviço Web referenciado.</span><span class="sxs-lookup"><span data-stu-id="899d5-105">When an XBAP is debugged from Visual Studio 2005, though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="899d5-106">Isso faz com que as exceções de segurança sejam geradas quando o XBAP tentar chamar o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="899d5-106">This causes security exceptions to be raised when the XBAP attempts to call the Web service.</span></span> <span data-ttu-id="899d5-107">No entanto, um projeto do WPF (aplicativo de navegador XAML) do Visual Studio 2005 pode ser configurado para simular ter o mesmo site de origem que o serviço Web que ele chama durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="899d5-107">However, a Visual Studio 2005 XAML Browser Application (WPF) project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="899d5-108">Isso permite que o XBAP chame com segurança o serviço Web sem causar exceções de segurança.</span><span class="sxs-lookup"><span data-stu-id="899d5-108">This allows the XBAP to safely call the Web service without causing security exceptions.</span></span>

## <a name="configuring-visual-studio"></a><span data-ttu-id="899d5-109">Configurando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="899d5-109">Configuring Visual Studio</span></span>
 <span data-ttu-id="899d5-110">Para configurar o Visual Studio 2005 para depurar um XBAP que chama um serviço Web:</span><span class="sxs-lookup"><span data-stu-id="899d5-110">To configure Visual Studio 2005 to debug an XBAP that calls a Web service:</span></span>

1. <span data-ttu-id="899d5-111">Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="899d5-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="899d5-112">No **Designer de Projeto**, clique na guia **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="899d5-112">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="899d5-113">Na seção **Iniciar Ação**, selecione **Iniciar programa externo** e insira o seguinte:</span><span class="sxs-lookup"><span data-stu-id="899d5-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>

     `C:\WINDOWS\System32\PresentationHost.exe`

4. <span data-ttu-id="899d5-114">Na seção **Opções de inicialização**, digite o seguinte na caixa de texto **Argumentos da linha de comando**:</span><span class="sxs-lookup"><span data-stu-id="899d5-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>

     <span data-ttu-id="899d5-115">*nome de arquivo* `-debug`</span><span class="sxs-lookup"><span data-stu-id="899d5-115">`-debug`  *filename*</span></span>

     <span data-ttu-id="899d5-116">O valor *filename* para o parâmetro **-debug** é o nome do arquivo .xbap; por exemplo:</span><span class="sxs-lookup"><span data-stu-id="899d5-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>

     `-debug c:\example.xbap`

> [!NOTE]
> <span data-ttu-id="899d5-117">Essa é a configuração padrão para soluções que são criadas com o modelo de projeto do WPF (aplicativo de navegador XAML) do Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="899d5-117">This is the default configuration for solutions that are created with the Visual Studio 2005 XAML Browser Application (WPF) project template.</span></span>

1. <span data-ttu-id="899d5-118">Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="899d5-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="899d5-119">No **Designer de Projeto**, clique na guia **Depurar**.</span><span class="sxs-lookup"><span data-stu-id="899d5-119">In the **Project Designer**, click the **Debug** tab.</span></span>

3. <span data-ttu-id="899d5-120">Na seção **Opções de inicialização**, adicione o seguinte parâmetro de linha de comando para a caixa de texto **Argumentos de linha de comando**:</span><span class="sxs-lookup"><span data-stu-id="899d5-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>

     <span data-ttu-id="899d5-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="899d5-121">`-debugSecurityZoneURL`  *URL*</span></span>

     <span data-ttu-id="899d5-122">O valor da *URL* para o parâmetro **-DEBUGSECURITYZONEURL** é a URL para o local que você deseja simular como sendo o site de origem do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="899d5-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the URL for the location that you want to simulate as being the site of origin of your application.</span></span>

 <span data-ttu-id="899d5-123">Como exemplo, considere um aplicativo de navegador XAML (XBAP) que usa um serviço Web com a seguinte URL:</span><span class="sxs-lookup"><span data-stu-id="899d5-123">As an example, consider a XAML browser application (XBAP) that uses a Web service with the following URL:</span></span>

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 <span data-ttu-id="899d5-124">A URL do site de origem para este serviço Web é:</span><span class="sxs-lookup"><span data-stu-id="899d5-124">The site of origin URL for this Web service is:</span></span>

 `http://services.msdn.microsoft.com`

 <span data-ttu-id="899d5-125">Consequentemente, o parâmetro de linha de comando completo **-debugSecurityZoneURL** e seu valor é:</span><span class="sxs-lookup"><span data-stu-id="899d5-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a><span data-ttu-id="899d5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="899d5-126">See also</span></span>

- [<span data-ttu-id="899d5-127">Host do WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="899d5-127">WPF Host (PresentationHost.exe)</span></span>](wpf-host-presentationhost-exe.md)

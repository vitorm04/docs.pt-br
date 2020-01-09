---
title: Host do WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 64ba1261134184f22e9faf157ca70e3471e3b3cb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636244"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="f716d-102">Host do WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="f716d-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="f716d-103">Windows Presentation Foundation (WPF) host (PresentationHost. exe) é o aplicativo que permite que os aplicativos do WPF sejam hospedados em navegadores compatíveis (incluindo o Microsoft Internet Explorer 6 e posterior).</span><span class="sxs-lookup"><span data-stu-id="f716d-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="f716d-104">Por padrão, o host do Windows Presentation Foundation (WPF) é registrado como o Shell e o manipulador de MIME para conteúdo WPF hospedado em navegador, que inclui:</span><span class="sxs-lookup"><span data-stu-id="f716d-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="f716d-105">Arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) flexíveis (não compilados).</span><span class="sxs-lookup"><span data-stu-id="f716d-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="f716d-106">Aplicativo de navegador XAML (XBAP) (. XBAP).</span><span class="sxs-lookup"><span data-stu-id="f716d-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="f716d-107">Para arquivos desses tipos, Windows Presentation Foundation (WPF) host:</span><span class="sxs-lookup"><span data-stu-id="f716d-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="f716d-108">Inicia o manipulador HTML registrado para hospedar o conteúdo do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f716d-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="f716d-109">Carrega as versões corretas dos assemblies Common Language Runtime (CLR) e Windows Presentation Foundation (WPF) necessários.</span><span class="sxs-lookup"><span data-stu-id="f716d-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="f716d-110">Garante que os níveis de permissão apropriados para a zona de implantação estejam em vigor.</span><span class="sxs-lookup"><span data-stu-id="f716d-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="f716d-111">Este tópico descreve os parâmetros de linha de comando que podem ser usados com PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="f716d-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f716d-112">Medição de</span><span class="sxs-lookup"><span data-stu-id="f716d-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="f716d-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f716d-113">Parameters</span></span>  
  
|<span data-ttu-id="f716d-114">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f716d-114">Parameter</span></span>|<span data-ttu-id="f716d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f716d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f716d-116">{1&gt;filename&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f716d-116">filename</span></span>|<span data-ttu-id="f716d-117">O caminho do arquivo a ser ativado.</span><span class="sxs-lookup"><span data-stu-id="f716d-117">The path of the file to be activated.</span></span> <span data-ttu-id="f716d-118">Também pode ser um URI.</span><span class="sxs-lookup"><span data-stu-id="f716d-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="f716d-119">-debug</span><span class="sxs-lookup"><span data-stu-id="f716d-119">-debug</span></span>|<span data-ttu-id="f716d-120">Ao ativar um aplicativo, não o confirme, nem o execute por meio do repositório.</span><span class="sxs-lookup"><span data-stu-id="f716d-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="f716d-121">Isso só funciona quando um arquivo local é ativado.</span><span class="sxs-lookup"><span data-stu-id="f716d-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="f716d-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="f716d-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="f716d-123">Usado com um valor de URL para indicar ao PresentationHost. exe que um aplicativo deve ser depurado como se fosse implantado a partir da URL especificada.</span><span class="sxs-lookup"><span data-stu-id="f716d-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="f716d-124">Isso determina a zona de implantação e o site de origem.</span><span class="sxs-lookup"><span data-stu-id="f716d-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="f716d-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="f716d-125">-embedding</span></span>|<span data-ttu-id="f716d-126">Exigido pelo OLE.</span><span class="sxs-lookup"><span data-stu-id="f716d-126">Required by OLE.</span></span> <span data-ttu-id="f716d-127">Se o parâmetro `-event` ou `-debug` estiver especificado, não será necessário especificar o parâmetro `-embedding`, já que esse parâmetro é definido internamente.</span><span class="sxs-lookup"><span data-stu-id="f716d-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="f716d-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="f716d-128">-event \<eventname></span></span>|<span data-ttu-id="f716d-129">Abra o evento com esse nome e o sinalize quando o PresentationHost. exe for inicializado e estiver pronto para hospedar o conteúdo do WPF.</span><span class="sxs-lookup"><span data-stu-id="f716d-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="f716d-130">O PresentationHost.exe será encerrado se houver um erro ao abrir o evento, tal como se ele ainda não tiver sido criado.</span><span class="sxs-lookup"><span data-stu-id="f716d-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="f716d-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="f716d-131">-launchApplication \<url></span></span>|<span data-ttu-id="f716d-132">Inicia um aplicativo ClickOnce autônomo a partir da URL especificada.</span><span class="sxs-lookup"><span data-stu-id="f716d-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="f716d-133">A política de segurança do Internet Explorer e WinINet relacionada a aplicativos .NET são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="f716d-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="f716d-134">Cenários</span><span class="sxs-lookup"><span data-stu-id="f716d-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="f716d-135">Manipulador de shell</span><span class="sxs-lookup"><span data-stu-id="f716d-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="f716d-136">Manipulador MIME</span><span class="sxs-lookup"><span data-stu-id="f716d-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="f716d-137">Depuração do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f716d-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="f716d-138">Depuração do Visual Studio na Zona</span><span class="sxs-lookup"><span data-stu-id="f716d-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="f716d-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="f716d-139">See also</span></span>

- [<span data-ttu-id="f716d-140">Security</span><span class="sxs-lookup"><span data-stu-id="f716d-140">Security</span></span>](../security-wpf.md)

---
title: Host do WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: d3b1ebf3cd62b77a9082c0b149469462b5dffa3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577503"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="79afb-102">Host do WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="79afb-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="79afb-103">Host do Windows Presentation Foundation (WPF) (PresentationHost.exe) é o aplicativo que permite [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos sejam hospedados em navegadores compatíveis (incluindo [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] e posterior).</span><span class="sxs-lookup"><span data-stu-id="79afb-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="79afb-104">Por padrão, o Host do Windows Presentation Foundation (WPF) é registrado como shell e [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] hospedados pelo navegador manipulador para [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] conteúdo, que inclui:</span><span class="sxs-lookup"><span data-stu-id="79afb-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
-   <span data-ttu-id="79afb-105">Arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) flexíveis (não compilados).</span><span class="sxs-lookup"><span data-stu-id="79afb-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="79afb-106">(.xbap).</span><span class="sxs-lookup"><span data-stu-id="79afb-106">(.xbap).</span></span>  
  
 <span data-ttu-id="79afb-107">Para arquivos desses tipos, o Host do Windows Presentation Foundation (WPF):</span><span class="sxs-lookup"><span data-stu-id="79afb-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
-   <span data-ttu-id="79afb-108">Inicia o registrado [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] manipulador para hospedar o conteúdo do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="79afb-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
-   <span data-ttu-id="79afb-109">Carrega as versões corretas necessárias [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] e assemblies do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="79afb-109">Loads the right versions of the required [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
-   <span data-ttu-id="79afb-110">Garante que os níveis de permissão apropriados para a zona de implantação estejam em vigor.</span><span class="sxs-lookup"><span data-stu-id="79afb-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="79afb-111">Este tópico descreve os parâmetros de linha de comando que podem ser usados com PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="79afb-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="79afb-112">Uso</span><span class="sxs-lookup"><span data-stu-id="79afb-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="79afb-113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79afb-113">Parameters</span></span>  
  
|<span data-ttu-id="79afb-114">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="79afb-114">Parameter</span></span>|<span data-ttu-id="79afb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="79afb-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79afb-116">filename</span><span class="sxs-lookup"><span data-stu-id="79afb-116">filename</span></span>|<span data-ttu-id="79afb-117">O caminho do arquivo a ser ativado.</span><span class="sxs-lookup"><span data-stu-id="79afb-117">The path of the file to be activated.</span></span> <span data-ttu-id="79afb-118">Também pode ser um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79afb-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="79afb-119">-debug</span><span class="sxs-lookup"><span data-stu-id="79afb-119">-debug</span></span>|<span data-ttu-id="79afb-120">Ao ativar um aplicativo, não o confirme, nem o execute por meio do repositório.</span><span class="sxs-lookup"><span data-stu-id="79afb-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="79afb-121">Isso só funciona quando um arquivo local é ativado.</span><span class="sxs-lookup"><span data-stu-id="79afb-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="79afb-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="79afb-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="79afb-123">Usado com um valor [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] para indicar ao PresentationHost.exe que um aplicativo deve ser depurado como se ele fosse implantado por meio do [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] especificado.</span><span class="sxs-lookup"><span data-stu-id="79afb-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="79afb-124">Isso determina a zona de implantação e o site de origem.</span><span class="sxs-lookup"><span data-stu-id="79afb-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="79afb-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="79afb-125">-embedding</span></span>|<span data-ttu-id="79afb-126">Exigido pelo OLE.</span><span class="sxs-lookup"><span data-stu-id="79afb-126">Required by OLE.</span></span> <span data-ttu-id="79afb-127">Se o parâmetro `-event` ou `-debug` estiver especificado, não será necessário especificar o parâmetro `-embedding`, já que esse parâmetro é definido internamente.</span><span class="sxs-lookup"><span data-stu-id="79afb-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="79afb-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="79afb-128">-event \<eventname></span></span>|<span data-ttu-id="79afb-129">Abra o evento com este nome e o sinalize quando o PresentationHost.exe for inicializado e estiver pronto para hospedar conteúdo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79afb-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="79afb-130">O PresentationHost.exe será encerrado se houver um erro ao abrir o evento, tal como se ele ainda não tiver sido criado.</span><span class="sxs-lookup"><span data-stu-id="79afb-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="79afb-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="79afb-131">-launchApplication \<url></span></span>|<span data-ttu-id="79afb-132">Inicia um aplicativo [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] autônomo da URL especificada.</span><span class="sxs-lookup"><span data-stu-id="79afb-132">Launches a standalone [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] application from the specified URL.</span></span> [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] <span data-ttu-id="79afb-133">e a política de segurança de WinINet sobre aplicativos .NET são aplicadas.</span><span class="sxs-lookup"><span data-stu-id="79afb-133">and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="79afb-134">Cenários</span><span class="sxs-lookup"><span data-stu-id="79afb-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="79afb-135">Manipulador de shell</span><span class="sxs-lookup"><span data-stu-id="79afb-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="79afb-136">Manipulador MIME</span><span class="sxs-lookup"><span data-stu-id="79afb-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="79afb-137">Depuração do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79afb-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="79afb-138">Depuração do Visual Studio na Zona</span><span class="sxs-lookup"><span data-stu-id="79afb-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="79afb-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79afb-139">See also</span></span>
- [<span data-ttu-id="79afb-140">Segurança</span><span class="sxs-lookup"><span data-stu-id="79afb-140">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)

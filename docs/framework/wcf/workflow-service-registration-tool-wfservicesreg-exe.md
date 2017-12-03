---
title: "Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6a009193a88c588a19c324353296a78e27617df
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="cdd31-102">Ferramenta de registro de serviço de fluxo de trabalho (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="cdd31-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="cdd31-103">Ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg.exe) é uma ferramenta autônoma que pode ser usada para adicionar, remover ou reparar os elementos de configuração para serviços do Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="cdd31-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd31-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdd31-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="cdd31-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdd31-105">Remarks</span></span>  
 <span data-ttu-id="cdd31-106">A ferramenta pode ser encontrada no [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] local de instalação, especificamente, % windir%\Microsoft.NET\Framework\v3.5, ou em %windir%\Microsoft.NET\Framework64\v3.5 em máquinas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="cdd31-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="cdd31-107">As tabelas a seguir descrevem as opções que podem ser usadas com a ferramenta de registro de serviços de fluxo de trabalho (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="cdd31-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="cdd31-108">Opção</span><span class="sxs-lookup"><span data-stu-id="cdd31-108">Option</span></span>|<span data-ttu-id="cdd31-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdd31-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="cdd31-110">Configurar os serviços de fluxo de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="cdd31-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="cdd31-111">Usado na instalação e reparar cenários.</span><span class="sxs-lookup"><span data-stu-id="cdd31-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="cdd31-112">Remove a configuração de serviços de fluxo de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="cdd31-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="cdd31-113">Imprima informações detalhadas (para configuração ou remoção).</span><span class="sxs-lookup"><span data-stu-id="cdd31-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="cdd31-114">Permite que o formato de log MSI.</span><span class="sxs-lookup"><span data-stu-id="cdd31-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="cdd31-115">Minimiza a janela quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="cdd31-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="cdd31-116">Registro</span><span class="sxs-lookup"><span data-stu-id="cdd31-116">Registration</span></span>  
 <span data-ttu-id="cdd31-117">A ferramenta inspeciona o arquivo Web. config e registra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cdd31-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
-   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<span data-ttu-id="cdd31-118">assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="cdd31-118"> reference assemblies.</span></span>  
  
-   <span data-ttu-id="cdd31-119">Um provedor de compilação para arquivos. xoml.</span><span class="sxs-lookup"><span data-stu-id="cdd31-119">A build provider for .xoml files.</span></span>  
  
-   <span data-ttu-id="cdd31-120">Manipuladores HTTP para arquivos xoml e. rules.</span><span class="sxs-lookup"><span data-stu-id="cdd31-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="cdd31-121">A ferramenta inspeciona o arquivo Machine. config e registra as seguintes extensões:</span><span class="sxs-lookup"><span data-stu-id="cdd31-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
-   <span data-ttu-id="cdd31-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="cdd31-122">behaviorExtensions</span></span>  
  
-   <span data-ttu-id="cdd31-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="cdd31-123">bindingElementExtensions</span></span>  
  
-   <span data-ttu-id="cdd31-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="cdd31-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="cdd31-125">A ferramenta também registra os seguintes importadores de metadados do cliente:</span><span class="sxs-lookup"><span data-stu-id="cdd31-125">The tool also registers the following client metadata importers:</span></span>  
  
-   <span data-ttu-id="cdd31-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="cdd31-126">policyImporters</span></span>  
  
-   <span data-ttu-id="cdd31-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="cdd31-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="cdd31-128">A ferramenta também registra manipuladores e mapas de script. xoml e. Rules na metabase do IIS.</span><span class="sxs-lookup"><span data-stu-id="cdd31-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="cdd31-129">Em [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../includes/wxp-md.md)] máquinas (IIS 5.1 e [!INCLUDE[iis601](../../../includes/iis601-md.md)]), um conjunto de. xoml e mapas de script. Rules são registrados.</span><span class="sxs-lookup"><span data-stu-id="cdd31-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and [!INCLUDE[iis601](../../../includes/iis601-md.md)]), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="cdd31-130">Em computadores de 64 bits, a ferramenta registra mapas de script de modo WOW se o `Enable32BitAppOnWin64` opção é habilitados ou nativos mapas de script de 64 bits, se o `Enable32BitAppOnWin64` está desativada.</span><span class="sxs-lookup"><span data-stu-id="cdd31-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="cdd31-131">Em [!INCLUDE[wv](../../../includes/wv-md.md)] e Windows Server 2008 (IIS 7.0 e posterior) máquinas, dois conjuntos de. xoml e. Rules manipuladores registradas: um para modo integrado e outro para o modo clássico.</span><span class="sxs-lookup"><span data-stu-id="cdd31-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="cdd31-132">Em computadores de 64 bits, três conjuntos de manipuladores registrados (independentemente do estado do `Enable32BitAppOnWin64` alternar): uma para o modo integrado, um para o modo WOW clássico e outro para o modo clássico 64 bits nativo.</span><span class="sxs-lookup"><span data-stu-id="cdd31-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdd31-133">Ao contrário de ServiceModelreg.exe, WFServicesReg.exe não permite adicionar, remover ou reparar os mapas de script ou manipuladores para um site específico.</span><span class="sxs-lookup"><span data-stu-id="cdd31-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="cdd31-134">Para uma solução alternativa para esse problema, consulte a seção "Como reparar os mapas de script".</span><span class="sxs-lookup"><span data-stu-id="cdd31-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="cdd31-135">Cenários de uso</span><span class="sxs-lookup"><span data-stu-id="cdd31-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="cdd31-136">Instalar o IIS após a instalação do .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="cdd31-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="cdd31-137">Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] máquina, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] está instalado antes da instalação do IIS.</span><span class="sxs-lookup"><span data-stu-id="cdd31-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="cdd31-138">Devido à indisponibilidade da metabase do IIS, instalação de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] terá êxito sem instalar os scriptmaps. xoml e. rules.</span><span class="sxs-lookup"><span data-stu-id="cdd31-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="cdd31-139">Depois que o IIS estiver instalado, você pode usar a ferramenta de WFServicesReg.exe com o `/c` switch para instalar esses mapas de script específicos.</span><span class="sxs-lookup"><span data-stu-id="cdd31-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="cdd31-140">Reparar os mapas de script</span><span class="sxs-lookup"><span data-stu-id="cdd31-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="cdd31-141">Mapa de script excluído no nó de Sites da Web</span><span class="sxs-lookup"><span data-stu-id="cdd31-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="cdd31-142">Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] máquina,. xoml ou. rules for excluído acidentalmente de nó de Sites da Web.</span><span class="sxs-lookup"><span data-stu-id="cdd31-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="cdd31-143">Isso pode ser reparado, executando a ferramenta WFServicesReg.exe com o `/c` alternar.</span><span class="sxs-lookup"><span data-stu-id="cdd31-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="cdd31-144">Mapa de script excluído em um site específico</span><span class="sxs-lookup"><span data-stu-id="cdd31-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="cdd31-145">Em um [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] máquina,. xoml ou. rules for excluído acidentalmente de um site específico (por exemplo, o Site padrão), em vez da partir do nó de Sites da Web.</span><span class="sxs-lookup"><span data-stu-id="cdd31-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="cdd31-146">Para reparar excluídos manipuladores para um site específico, você deve executar "WFServicesReg.exe r" para remover manipuladores de todos os sites da Web, em seguida, execute "WFServicesReg.exe c" para criar os manipuladores apropriados para todos os sites da Web.</span><span class="sxs-lookup"><span data-stu-id="cdd31-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="cdd31-147">Configurando manipuladores depois de alternar o modo IIS</span><span class="sxs-lookup"><span data-stu-id="cdd31-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="cdd31-148">Quando o IIS está no modo de configuração compartilhada e [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] é instalado, a metabase do IIS é configurado em um local compartilhado.</span><span class="sxs-lookup"><span data-stu-id="cdd31-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="cdd31-149">Se você alternar o IIS para o modo de configuração não compartilhado, a metabase local não conterá os manipuladores necessários.</span><span class="sxs-lookup"><span data-stu-id="cdd31-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="cdd31-150">Para configurar a metabase local corretamente, importe a metabase compartilhado no local, ou execute "WFServicesReg.exe /c", que configura a metabase local.</span><span class="sxs-lookup"><span data-stu-id="cdd31-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>

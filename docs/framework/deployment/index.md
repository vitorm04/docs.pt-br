---
title: Implantando o .NET Framework e aplicativos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
caps.latest.revision: "56"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eee16adfaa38b9a616f47d8489d99d0d9714cbaa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="91d00-102">Implantando o .NET Framework e aplicativos</span><span class="sxs-lookup"><span data-stu-id="91d00-102">Deploying the .NET Framework and Applications</span></span>
<span data-ttu-id="91d00-103">Este artigo ajuda você a começar a implantar o .NET Framework com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91d00-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="91d00-104">A maioria das informações destina-se a desenvolvedores, OEMs e administradores corporativos.</span><span class="sxs-lookup"><span data-stu-id="91d00-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="91d00-105">Os usuários que desejam instalar o .NET Framework nos respectivos computadores devem ler o artigo [Instalando o .NET Framework](~/docs/framework/install/index.md).</span><span class="sxs-lookup"><span data-stu-id="91d00-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](~/docs/framework/install/index.md).</span></span>  
  
## <a name="key-deployment-resources"></a><span data-ttu-id="91d00-106">Principais recursos de implantação</span><span class="sxs-lookup"><span data-stu-id="91d00-106">Key Deployment Resources</span></span>  
 <span data-ttu-id="91d00-107">Use os links a seguir para outros tópicos do MSDN e veja as informações específicas sobre como implantar e prestar assistência ao .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91d00-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>  
  
 <span data-ttu-id="91d00-108">**Configuração e implantação**</span><span class="sxs-lookup"><span data-stu-id="91d00-108">**Setup and deployment**</span></span>  
  
-   <span data-ttu-id="91d00-109">Informações gerais sobre o instalador e a implantação:</span><span class="sxs-lookup"><span data-stu-id="91d00-109">General installer and deployment information:</span></span>  
  
    -   <span data-ttu-id="91d00-110">Opções do instalador:</span><span class="sxs-lookup"><span data-stu-id="91d00-110">Installer options:</span></span>  
  
        -   [<span data-ttu-id="91d00-111">Instalador da Web</span><span class="sxs-lookup"><span data-stu-id="91d00-111">Web installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [<span data-ttu-id="91d00-112">Instalador offline</span><span class="sxs-lookup"><span data-stu-id="91d00-112">Offline installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   <span data-ttu-id="91d00-113">Modos de instalação:</span><span class="sxs-lookup"><span data-stu-id="91d00-113">Installation modes:</span></span>  
  
        -   [<span data-ttu-id="91d00-114">Instalação silenciosa</span><span class="sxs-lookup"><span data-stu-id="91d00-114">Silent installation</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [<span data-ttu-id="91d00-115">Exibição de uma interface do usuário</span><span class="sxs-lookup"><span data-stu-id="91d00-115">Displaying a UI</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [<span data-ttu-id="91d00-116">Redução de reinicializações do sistema durante instalações do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="91d00-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [<span data-ttu-id="91d00-117">Solução de problemas de instalações e desinstalações bloqueadas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="91d00-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   <span data-ttu-id="91d00-118">Implantação do .NET Framework com um aplicativo cliente (para desenvolvedores):</span><span class="sxs-lookup"><span data-stu-id="91d00-118">Deploying the .NET Framework with a client application (for developers):</span></span>  
  
    -   <span data-ttu-id="91d00-119">[Uso do InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) em um projeto de configuração e implantação</span><span class="sxs-lookup"><span data-stu-id="91d00-119">[Using InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>  
  
    -   [<span data-ttu-id="91d00-120">Uso de um aplicativo ClickOnce do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="91d00-120">Using a Visual Studio ClickOnce application</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [<span data-ttu-id="91d00-121">Criação de um pacote de instalação WiX</span><span class="sxs-lookup"><span data-stu-id="91d00-121">Creating a WiX installation package</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [<span data-ttu-id="91d00-122">Uso de um instalador personalizado</span><span class="sxs-lookup"><span data-stu-id="91d00-122">Using a custom installer</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   <span data-ttu-id="91d00-123">[Informações adicionais](../../../docs/framework/deployment/deployment-guide-for-developers.md) para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="91d00-123">[Additional information](../../../docs/framework/deployment/deployment-guide-for-developers.md) for developers</span></span>  
  
-   <span data-ttu-id="91d00-124">Implantação do .NET Framework (para OEMs e administradores):</span><span class="sxs-lookup"><span data-stu-id="91d00-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>  
  
    -   [<span data-ttu-id="91d00-125">Windows ADK (Kit de Avaliação e Implantação do Windows)</span><span class="sxs-lookup"><span data-stu-id="91d00-125">Windows Assessment and Deployment Kit (ADK)</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [<span data-ttu-id="91d00-126">Guia do administrador</span><span class="sxs-lookup"><span data-stu-id="91d00-126">Administrator's guide</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 <span data-ttu-id="91d00-127">**Manutenção**</span><span class="sxs-lookup"><span data-stu-id="91d00-127">**Servicing**</span></span>  
  
-   <span data-ttu-id="91d00-128">Para obter informações gerais, confira o [blog do .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=254977)</span><span class="sxs-lookup"><span data-stu-id="91d00-128">For general information, see the [.NET Framework blog](http://go.microsoft.com/fwlink/p/?LinkId=254977)</span></span>  
  
-   [<span data-ttu-id="91d00-129">Como detectar versões</span><span class="sxs-lookup"><span data-stu-id="91d00-129">Detecting versions</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [<span data-ttu-id="91d00-130">Como detectar service packs e atualizações</span><span class="sxs-lookup"><span data-stu-id="91d00-130">Detecting service packs and updates</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a><span data-ttu-id="91d00-131">Recursos que simplificam a implantação</span><span class="sxs-lookup"><span data-stu-id="91d00-131">Features That Simplify Deployment</span></span>  
 <span data-ttu-id="91d00-132">O .NET Framework fornece vários recursos básicos que facilitam a implantação de aplicativos:</span><span class="sxs-lookup"><span data-stu-id="91d00-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>  
  
-   <span data-ttu-id="91d00-133">Aplicativos sem impacto.</span><span class="sxs-lookup"><span data-stu-id="91d00-133">No-impact applications.</span></span>  
  
     <span data-ttu-id="91d00-134">Esse recurso fornece isolamento de aplicativo e elimina conflitos de DLL.</span><span class="sxs-lookup"><span data-stu-id="91d00-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="91d00-135">Por padrão, os componentes não afetam outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="91d00-135">By default, components do not affect other applications.</span></span>  
  
-   <span data-ttu-id="91d00-136">Componentes privados por padrão.</span><span class="sxs-lookup"><span data-stu-id="91d00-136">Private components by default.</span></span>  
  
     <span data-ttu-id="91d00-137">Por padrão, os componentes são implantados no diretório de aplicativo e ficam visíveis apenas para o aplicativo que os contém.</span><span class="sxs-lookup"><span data-stu-id="91d00-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>  
  
-   <span data-ttu-id="91d00-138">Compartilhamento de código controlado.</span><span class="sxs-lookup"><span data-stu-id="91d00-138">Controlled code sharing.</span></span>  
  
     <span data-ttu-id="91d00-139">O compartilhamento de código exige que você disponibilize explicitamente o código para compartilhamento em vez de ser o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="91d00-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>  
  
-   <span data-ttu-id="91d00-140">Controle de versão lado a lado.</span><span class="sxs-lookup"><span data-stu-id="91d00-140">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="91d00-141">É possível a coexistência de várias versões de um componente ou aplicativo. Você pode escolher quais versões usar e o Common Language Runtime impõe a política de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="91d00-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>  
  
-   <span data-ttu-id="91d00-142">Implantação e replicação de XCOPY.</span><span class="sxs-lookup"><span data-stu-id="91d00-142">XCOPY deployment and replication.</span></span>  
  
     <span data-ttu-id="91d00-143">Os aplicativos e componentes autodescritos e autossuficientes podem ser implantados sem entradas nem dependências de Registro.</span><span class="sxs-lookup"><span data-stu-id="91d00-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>  
  
-   <span data-ttu-id="91d00-144">Atualizações dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="91d00-144">On-the-fly updates.</span></span>  
  
     <span data-ttu-id="91d00-145">Os administradores podem usar hosts, como o ASP.NET, para atualizar DLLs de programa, mesmo em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="91d00-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>  
  
-   <span data-ttu-id="91d00-146">Integração ao Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="91d00-146">Integration with the Windows Installer.</span></span>  
  
     <span data-ttu-id="91d00-147">O anúncio, a publicação, o reparo e a instalação sob demanda estão disponíveis na implantação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91d00-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>  
  
-   <span data-ttu-id="91d00-148">Implantação corporativa.</span><span class="sxs-lookup"><span data-stu-id="91d00-148">Enterprise deployment.</span></span>  
  
     <span data-ttu-id="91d00-149">Esse recurso permite a fácil distribuição de software, incluindo o uso do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="91d00-149">This feature provides easy software distribution, including using Active Directory.</span></span>  
  
-   <span data-ttu-id="91d00-150">Download e armazenamento em cache.</span><span class="sxs-lookup"><span data-stu-id="91d00-150">Downloading and caching.</span></span>  
  
     <span data-ttu-id="91d00-151">Os downloads incrementais reduzem o tamanho dos downloads, e os componentes podem ser isolados apenas para uso do aplicativo para implantação de baixo impacto.</span><span class="sxs-lookup"><span data-stu-id="91d00-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>  
  
-   <span data-ttu-id="91d00-152">Código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="91d00-152">Partially trusted code.</span></span>  
  
     <span data-ttu-id="91d00-153">A identidade se baseia no código, e não no usuário, e nenhuma caixa de diálogo de certificado é exibida.</span><span class="sxs-lookup"><span data-stu-id="91d00-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>  
  
## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="91d00-154">Empacotando e distribuindo aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="91d00-154">Packaging and Distributing .NET Framework Applications</span></span>  
 <span data-ttu-id="91d00-155">Algumas das informações de empacotamento e implantação para o .NET Framework são descritas em outras seções da documentação.</span><span class="sxs-lookup"><span data-stu-id="91d00-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="91d00-156">Essas seções fornecem informações sobre a autodescrição das unidades chamadas [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), que não exigem entradas de Registro, os [assemblies com nome forte](../../../docs/framework/app-domains/strong-named-assemblies.md), que garantem a exclusividade do nome e impedem sua falsificação, e o [controle de versão do assembly](../../../docs/framework/app-domains/assembly-versioning.md), que soluciona muitos dos problemas associados ao conflitos de DLL.</span><span class="sxs-lookup"><span data-stu-id="91d00-156">Those sections provide information about the self-describing units called [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), which require no registry entries, [strong-named assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../../docs/framework/app-domains/assembly-versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="91d00-157">As seções a seguir fornecem informações sobre empacotamento e distribuição de aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91d00-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>  
  
### <a name="packaging"></a><span data-ttu-id="91d00-158">Packaging</span><span class="sxs-lookup"><span data-stu-id="91d00-158">Packaging</span></span>  
 <span data-ttu-id="91d00-159">O .NET Framework fornece as seguintes opções para empacotamento de aplicativos:</span><span class="sxs-lookup"><span data-stu-id="91d00-159">The .NET Framework provides the following options for packaging applications:</span></span>  
  
-   <span data-ttu-id="91d00-160">Como um único assembly ou uma coleção de assemblies.</span><span class="sxs-lookup"><span data-stu-id="91d00-160">As a single assembly or as a collection of assemblies.</span></span>  
  
     <span data-ttu-id="91d00-161">Com essa opção, você simplesmente usa os arquivos .dll ou .exe como eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="91d00-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>  
  
-   <span data-ttu-id="91d00-162">Como arquivos de gabinete (CAB).</span><span class="sxs-lookup"><span data-stu-id="91d00-162">As cabinet (CAB) files.</span></span>  
  
     <span data-ttu-id="91d00-163">Com essa opção, você pode compactar arquivos em arquivos .cab para que a distribuição ou o download leve menos tempo.</span><span class="sxs-lookup"><span data-stu-id="91d00-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>  
  
-   <span data-ttu-id="91d00-164">Como um pacote do Windows Installer ou em outros formatos de instalador.</span><span class="sxs-lookup"><span data-stu-id="91d00-164">As a Windows Installer package or in other installer formats.</span></span>  
  
     <span data-ttu-id="91d00-165">Com essa opção, você cria arquivos .msi para uso com o Windows Installer ou empacota o aplicativo para uso com algum outro instalador.</span><span class="sxs-lookup"><span data-stu-id="91d00-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>  
  
### <a name="distribution"></a><span data-ttu-id="91d00-166">Distribuição</span><span class="sxs-lookup"><span data-stu-id="91d00-166">Distribution</span></span>  
 <span data-ttu-id="91d00-167">O .NET Framework fornece as seguintes opções para distribuição de aplicativos:</span><span class="sxs-lookup"><span data-stu-id="91d00-167">The .NET Framework provides the following options for distributing applications:</span></span>  
  
-   <span data-ttu-id="91d00-168">Usar XCOPY ou FTP.</span><span class="sxs-lookup"><span data-stu-id="91d00-168">Use XCOPY or FTP.</span></span>  
  
     <span data-ttu-id="91d00-169">Como os aplicativos Common Language Runtime são autodescritivos e não exigem entradas de Registro, você pode usar o XCOPY ou o FTP para simplesmente copiar o aplicativo para um diretório apropriado.</span><span class="sxs-lookup"><span data-stu-id="91d00-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="91d00-170">Assim, o aplicativo pode ser executado nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="91d00-170">The application can then be run from that directory.</span></span>  
  
-   <span data-ttu-id="91d00-171">Usar o download de código.</span><span class="sxs-lookup"><span data-stu-id="91d00-171">Use code download.</span></span>  
  
     <span data-ttu-id="91d00-172">Se você estiver distribuindo o aplicativo pela Internet ou por meio de uma intranet corporativa, basta baixar o código em um computador e executar o aplicativo nele.</span><span class="sxs-lookup"><span data-stu-id="91d00-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>  
  
-   <span data-ttu-id="91d00-173">Usar um programa de instalação, como o Windows Installer 2.0.</span><span class="sxs-lookup"><span data-stu-id="91d00-173">Use an installer program such as Windows Installer 2.0.</span></span>  
  
     <span data-ttu-id="91d00-174">O Windows Installer 2.0 pode instalar, reparar ou remover assemblies do .NET Framework no cache de assembly global e em diretórios privados.</span><span class="sxs-lookup"><span data-stu-id="91d00-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>  
  
### <a name="installation-location"></a><span data-ttu-id="91d00-175">Local de instalação</span><span class="sxs-lookup"><span data-stu-id="91d00-175">Installation Location</span></span>  
 <span data-ttu-id="91d00-176">Para determinar onde implantar assemblies do aplicativo para que eles possam ser encontrados pelo tempo de execução, confira [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="91d00-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="91d00-177">As considerações de segurança também podem afetar como você implanta o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91d00-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="91d00-178">As permissões de segurança são concedidas ao código gerenciado de acordo com o local do código.</span><span class="sxs-lookup"><span data-stu-id="91d00-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="91d00-179">Implantar um aplicativo ou componente em um local em que ele recebe pouca confiança, como a Internet, limita o que o aplicativo ou componente pode fazer.</span><span class="sxs-lookup"><span data-stu-id="91d00-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="91d00-180">Para saber mais sobre considerações de implantação e segurança, confira [Noções básicas sobre segurança de acesso do código](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="91d00-180">For more information about deployment and security considerations, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="91d00-181">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="91d00-181">Related Topics</span></span>  
  
|<span data-ttu-id="91d00-182">Título</span><span class="sxs-lookup"><span data-stu-id="91d00-182">Title</span></span>|<span data-ttu-id="91d00-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="91d00-183">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="91d00-184">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="91d00-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|<span data-ttu-id="91d00-185">Descreve como o Common Language Runtime determina qual assembly usar para atender a uma solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="91d00-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|  
|[<span data-ttu-id="91d00-186">Práticas recomendadas para carregamento de assemblies</span><span class="sxs-lookup"><span data-stu-id="91d00-186">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<span data-ttu-id="91d00-187">Descreve maneiras de evitar problemas de identidade de tipo que podem levar a <xref:System.InvalidCastException>, <xref:System.MissingMethodException> e outros erros.</span><span class="sxs-lookup"><span data-stu-id="91d00-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|  
|[<span data-ttu-id="91d00-188">Redução de reinicializações do sistema durante instalações do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="91d00-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)|<span data-ttu-id="91d00-189">Descreve o Gerenciador de Reinicialização, que impede reinicializações sempre que possível, além de explicar como os aplicativos que instalam o .NET Framework podem aproveitá-lo.</span><span class="sxs-lookup"><span data-stu-id="91d00-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|  
|[<span data-ttu-id="91d00-190">Guia de implantação para administradores</span><span class="sxs-lookup"><span data-stu-id="91d00-190">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)|<span data-ttu-id="91d00-191">Explica como um administrador de sistema pode implantar o .NET Framework e suas dependências de sistema em uma rede usando o SCCM (System Center Configuration Manager).</span><span class="sxs-lookup"><span data-stu-id="91d00-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>|  
|[<span data-ttu-id="91d00-192">Guia de implantação para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="91d00-192">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)|<span data-ttu-id="91d00-193">Explica como os desenvolvedores podem instalar o .NET Framework nos computadores dos usuários com seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="91d00-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|  
|[<span data-ttu-id="91d00-194">Implantando aplicativos, serviços e componentes</span><span class="sxs-lookup"><span data-stu-id="91d00-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="91d00-195">Aborda as opções de implantação no Visual Studio, incluindo instruções para publicar um aplicativo usando as tecnologias ClickOnce e Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="91d00-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>| 
|[<span data-ttu-id="91d00-196">Publicando aplicativos ClickOnce</span><span class="sxs-lookup"><span data-stu-id="91d00-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="91d00-197">Descreve como empacotar um aplicativo do Windows Forms e implantá-lo com o ClickOnce em computadores cliente em uma rede.</span><span class="sxs-lookup"><span data-stu-id="91d00-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|  
|[<span data-ttu-id="91d00-198">Empacotando e implantando recursos</span><span class="sxs-lookup"><span data-stu-id="91d00-198">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="91d00-199">Descreve o modelo de hub e spoke usado pelo .NET Framework para empacotar e implantar recursos; aborda convenções de nomenclatura de recurso, processo de fallback e alternativas de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="91d00-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|  
|[<span data-ttu-id="91d00-200">Implantação de um aplicativo de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="91d00-200">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)|<span data-ttu-id="91d00-201">Explica como enviar e instalar aplicativos de interoperabilidade, que geralmente incluem um assembly de cliente do .NET Framework, um ou mais assemblies de interoperabilidade que representam diferentes bibliotecas de tipo COM e um ou mais componentes COM registrados.</span><span class="sxs-lookup"><span data-stu-id="91d00-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|  
|[<span data-ttu-id="91d00-202">Como acompanhar o progresso do instalador do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="91d00-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="91d00-203">Descreve como inicializar e rastrear silenciosamente o processo de instalação do .NET Framework ao mesmo tempo que mostra sua própria exibição do progresso de instalação.</span><span class="sxs-lookup"><span data-stu-id="91d00-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91d00-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91d00-204">See Also</span></span>  
 [<span data-ttu-id="91d00-205">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="91d00-205">Development Guide</span></span>](../../../docs/framework/development-guide.md)

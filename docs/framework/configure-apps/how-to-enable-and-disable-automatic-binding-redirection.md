---
title: Como habilitar e desabilitar o redirecionamento automático de associações
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d71da1b48938f9f98221d86f0f9badee3a17919
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="f0718-102">Como habilitar e desabilitar o redirecionamento automático de associações</span><span class="sxs-lookup"><span data-stu-id="f0718-102">How to: Enable and Disable Automatic Binding Redirection</span></span>
<span data-ttu-id="f0718-103">A partir do [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], quando você compila aplicativos destinados ao [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], os redirecionamentos de associação podem ser automaticamente adicionados ao arquivo de configuração do aplicativo para unificação do assembly de substituição.</span><span class="sxs-lookup"><span data-stu-id="f0718-103">Starting with [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], when you compile apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="f0718-104">Redirecionamentos de associação serão adicionados se o seu aplicativo ou seus componentes fizerem referência a mais de uma versão do mesmo assembly, mesmo se você especificar manualmente redirecionamentos de associação no arquivo de configuração para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0718-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="f0718-105">O recurso de redirecionamento de associação automático afeta os aplicativos tradicionais da área de trabalho que usam o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], embora o comportamento seja um pouco diferente para um aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="f0718-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="f0718-106">Você pode habilitar o redirecionamento de associação automático se houver aplicativos que usem versões anteriores do .NET Framework ou pode desativar esse recurso se desejar manter redirecionamentos manuais de associações criadas.</span><span class="sxs-lookup"><span data-stu-id="f0718-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="f0718-107">Desabilitando redirecionamentos de associação automáticos em aplicativos da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0718-107">Disabling automatic binding redirects in desktop apps</span></span>  
 <span data-ttu-id="f0718-108">Os redirecionamentos de associação automáticos são habilitados por padrão para aplicativos tradicionais da área de trabalho que usam o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="f0718-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="f0718-109">Os redirecionamentos de associação são adicionadas ao arquivo de configuração de saída (app.config) quando o aplicativo é compilado e substituem a unificação do assembly que pode ocorrer de outra forma.</span><span class="sxs-lookup"><span data-stu-id="f0718-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="f0718-110">O arquivo de origem app.config não é modificado.</span><span class="sxs-lookup"><span data-stu-id="f0718-110">The source app.config file is not modified.</span></span> <span data-ttu-id="f0718-111">Você pode desativar esse recurso ao modificar o arquivo de projeto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0718-111">You can disable this feature by modifying the project file for the app.</span></span>  
  
#### <a name="to-disable-automatic-binding-redirects"></a><span data-ttu-id="f0718-112">Para desativar os redirecionamentos de associação automáticos</span><span class="sxs-lookup"><span data-stu-id="f0718-112">To disable automatic binding redirects</span></span>  
  
1.  <span data-ttu-id="f0718-113">No Visual Studio, selecione o projeto em **Solution Explorer**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="f0718-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f0718-114">No Explorador de Arquivos, localize o arquivo de projeto (.csproj ou .vbproj) e o abra no Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="f0718-114">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="f0718-115">No arquivo de projeto, localize a seguinte entrada de propriedade:</span><span class="sxs-lookup"><span data-stu-id="f0718-115">In the project file, find the following property entry:</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  <span data-ttu-id="f0718-116">Altere `true` para `false`:</span><span class="sxs-lookup"><span data-stu-id="f0718-116">Change `true` to `false`:</span></span>  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a><span data-ttu-id="f0718-117">Habilitando redirecionamentos de associação automáticos manualmente</span><span class="sxs-lookup"><span data-stu-id="f0718-117">Enabling automatic binding redirects manually</span></span>  
 <span data-ttu-id="f0718-118">Você pode habilitar redirecionamentos de associação automáticos em aplicativos existentes destinados a versões anteriores do .NET Framework ou caso o sistema não solicite automaticamente a adição de um redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="f0718-118">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you are not automatically prompted to add a redirect.</span></span> <span data-ttu-id="f0718-119">Se seu aplicativo for destinado a uma versão mais recente da estrutura, mas o sistema não solicitar automaticamente a adição de um redirecionamento, provavelmente, a saída de compilação solicitará o remapeamento dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="f0718-119">If you are targeting a newer version of the framework but do not get automatically prompted to add a redirect, you will likely get   build output that suggests you remap assemblies.</span></span>  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a><span data-ttu-id="f0718-120">Para adicionar uma propriedade de redirecionamento de associação automático manualmente</span><span class="sxs-lookup"><span data-stu-id="f0718-120">To manually add an automatic binding redirect property</span></span>  
  
1.  <span data-ttu-id="f0718-121">No Visual Studio, selecione o projeto em **Solution Explorer**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="f0718-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f0718-122">No Explorador de Arquivos, localize o arquivo de projeto (.csproj ou .vbproj) e o abra no Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="f0718-122">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="f0718-123">Adicione o seguinte elemento para o primeiro grupo de propriedade de configuração (sob o \<PropertyGroup > marca):</span><span class="sxs-lookup"><span data-stu-id="f0718-123">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     <span data-ttu-id="f0718-124">O código a seguir mostra um exemplo de arquivo de projeto com o elemento.</span><span class="sxs-lookup"><span data-stu-id="f0718-124">The following shows an example project file with the element inserted.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProjectGuid>{123334}</ProjectGuid>  
        ...  
        <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>  
      </PropertyGroup>  
    ...  
    </Project>  
    ```  
  
4.  <span data-ttu-id="f0718-125">Compile seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0718-125">Compile your app.</span></span>  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="f0718-126">Habilitando redirecionamentos de associação automáticos em aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="f0718-126">Enabling automatic binding redirects in web apps</span></span>  
 <span data-ttu-id="f0718-127">Redirecionamentos de associação automáticos são implementados de maneira diferente para aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="f0718-127">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="f0718-128">Como o arquivo de configuração de origem (web.config) deve ser modificado para aplicativos Web, redirecionamentos de associação não são adicionados automaticamente ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f0718-128">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="f0718-129">Entretanto, o Visual Studio o notifica sobre conflitos de associação e você pode adicionar redirecionamentos de associação para resolver os conflitos.</span><span class="sxs-lookup"><span data-stu-id="f0718-129">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="f0718-130">Como você é sempre solicitado a adicionar redirecionamentos de associação, não é necessário desativar explicitamente esse recurso para um aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="f0718-130">Because you are always prompted to add binding redirects, you do not need to explicitly disable this feature for a web app.</span></span>  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a><span data-ttu-id="f0718-131">Para adicionar redirecionamentos de associação a um arquivo web.config</span><span class="sxs-lookup"><span data-stu-id="f0718-131">To add binding redirects to a web.config file</span></span>  
  
1.  <span data-ttu-id="f0718-132">No Visual Studio, compile o aplicativo e verifique a existência de avisos de compilação.</span><span class="sxs-lookup"><span data-stu-id="f0718-132">In Visual Studio, compile the app, and check for build warnings.</span></span>  
  
     <span data-ttu-id="f0718-133">![Aviso de conflitos de referência de assembly de compilação](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="f0718-133">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>  
  
2.  <span data-ttu-id="f0718-134">Se houver conflitos de associação de assembly, um aviso será exibido.</span><span class="sxs-lookup"><span data-stu-id="f0718-134">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="f0718-135">Clique duas vezes no aviso.</span><span class="sxs-lookup"><span data-stu-id="f0718-135">Double-click the warning.</span></span> <span data-ttu-id="f0718-136">(Teclado: selecione o aviso e pressione **Enter**.)</span><span class="sxs-lookup"><span data-stu-id="f0718-136">(Keyboard: Select the warning and press **Enter**.)</span></span>  
  
     <span data-ttu-id="f0718-137">Uma caixa de diálogo que permite adicionar automaticamente os redirecionamentos da associação necessários ao arquivo web.config de origem é exibida.</span><span class="sxs-lookup"><span data-stu-id="f0718-137">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>  
  
     <span data-ttu-id="f0718-138">![Caixa de diálogo de permissões de redirecionamento de associação](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="f0718-138">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0718-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0718-139">See Also</span></span>  
 [<span data-ttu-id="f0718-140">\<bindingRedirect > elemento</span><span class="sxs-lookup"><span data-stu-id="f0718-140">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [<span data-ttu-id="f0718-141">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="f0718-141">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)

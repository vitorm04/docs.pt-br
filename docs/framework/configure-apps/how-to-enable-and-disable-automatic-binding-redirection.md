---
title: Como habilitar e desabilitar o redirecionamento automático de associações
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9b9c9cbdb89ccf67942dcccee37ea410c6fa39a5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079537"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="374b8-102">Como habilitar e desabilitar o redirecionamento automático de associações</span><span class="sxs-lookup"><span data-stu-id="374b8-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="374b8-103">Quando você compila aplicativos no Visual Studio que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores, redirecionamentos de associação poderão ser automaticamente adicionadas ao arquivo de configuração de aplicativo para substituir a Unificação do assembly.</span><span class="sxs-lookup"><span data-stu-id="374b8-103">When you compile apps in Visual Studio that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="374b8-104">Redirecionamentos de associação serão adicionados se o seu aplicativo ou seus componentes fizerem referência a mais de uma versão do mesmo assembly, mesmo se você especificar manualmente redirecionamentos de associação no arquivo de configuração para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="374b8-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="374b8-105">O recurso de redirecionamento de associação automático afeta aplicativos de desktop tradicionais e aplicativos web que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ou uma versão posterior, embora o comportamento é ligeiramente diferente para um aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="374b8-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="374b8-106">Você pode habilitar o redirecionamento de associação automático se houver aplicativos que usem versões anteriores do .NET Framework ou pode desativar esse recurso se desejar manter redirecionamentos manuais de associações criadas.</span><span class="sxs-lookup"><span data-stu-id="374b8-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="374b8-107">Desabilitar os redirecionamentos de associação automáticos em aplicativos da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="374b8-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="374b8-108">Os redirecionamentos de associação automáticos são habilitados por padrão para aplicativos tradicionais da área de trabalho que usam o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="374b8-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="374b8-109">Os redirecionamentos de associação são adicionadas ao arquivo de configuração de saída (app.config) quando o aplicativo é compilado e substituem a unificação do assembly que pode ocorrer de outra forma.</span><span class="sxs-lookup"><span data-stu-id="374b8-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="374b8-110">O arquivo de origem app.config não é modificado.</span><span class="sxs-lookup"><span data-stu-id="374b8-110">The source app.config file is not modified.</span></span> <span data-ttu-id="374b8-111">Você pode desativar esse recurso ao modificar o arquivo de projeto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="374b8-111">You can disable this feature by modifying the project file for the app.</span></span>

1. <span data-ttu-id="374b8-112">Abra o arquivo de projeto para edição usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="374b8-112">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="374b8-113">No Visual Studio, selecione o projeto no **Gerenciador de soluções**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="374b8-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="374b8-114">No Explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abri-lo no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="374b8-114">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="374b8-115">No Visual Studio, no **Gerenciador de soluções**, clique com botão direito no projeto e escolha **descarregar projeto**.</span><span class="sxs-lookup"><span data-stu-id="374b8-115">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="374b8-116">Clique com botão direito do projeto descarregado novamente e, em seguida, escolha **Editar [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="374b8-116">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="374b8-117">No arquivo de projeto, localize a seguinte entrada de propriedade:</span><span class="sxs-lookup"><span data-stu-id="374b8-117">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="374b8-118">Altere `true` para `false`:</span><span class="sxs-lookup"><span data-stu-id="374b8-118">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="374b8-119">Habilitar redirecionamentos de associação automáticos manualmente</span><span class="sxs-lookup"><span data-stu-id="374b8-119">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="374b8-120">Você pode habilitar redirecionamentos de associação automáticos em aplicativos existentes destinados a versões anteriores do .NET Framework, ou em casos em que você é automaticamente solicitado a adicionar um redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="374b8-120">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="374b8-121">Se você estiver visando uma versão mais recente do framework, mas não solicitar automaticamente a adição de um redirecionamento, você provavelmente obterá saída de compilação que solicitará o remapeamento assemblies.</span><span class="sxs-lookup"><span data-stu-id="374b8-121">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="374b8-122">Abra o arquivo de projeto para edição usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="374b8-122">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="374b8-123">No Visual Studio, selecione o projeto no **Gerenciador de soluções**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="374b8-123">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="374b8-124">No Explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abri-lo no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="374b8-124">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="374b8-125">No Visual Studio, no **Gerenciador de soluções**, clique com botão direito no projeto e escolha **descarregar projeto**.</span><span class="sxs-lookup"><span data-stu-id="374b8-125">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="374b8-126">Clique com botão direito do projeto descarregado novamente e, em seguida, escolha **Editar [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="374b8-126">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="374b8-127">Adicione o seguinte elemento ao primeiro grupo de propriedades de configuração (sob o \<PropertyGroup > marca):</span><span class="sxs-lookup"><span data-stu-id="374b8-127">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="374b8-128">A seguir mostra um exemplo de arquivo de projeto com o elemento inserido:</span><span class="sxs-lookup"><span data-stu-id="374b8-128">The following shows an example project file with the element inserted:</span></span>

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

3. <span data-ttu-id="374b8-129">Compile seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="374b8-129">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="374b8-130">Habilitar redirecionamentos de associação automáticos em aplicativos web</span><span class="sxs-lookup"><span data-stu-id="374b8-130">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="374b8-131">Redirecionamentos de associação automáticos são implementados de maneira diferente para aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="374b8-131">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="374b8-132">Como o arquivo de configuração de origem (web.config) deve ser modificado para aplicativos Web, redirecionamentos de associação não são adicionados automaticamente ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="374b8-132">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="374b8-133">Entretanto, o Visual Studio o notifica sobre conflitos de associação e você pode adicionar redirecionamentos de associação para resolver os conflitos.</span><span class="sxs-lookup"><span data-stu-id="374b8-133">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="374b8-134">Como sempre, você será solicitado a adicionar redirecionamentos de associação, você não precisa desabilitar explicitamente esse recurso para um aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="374b8-134">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="374b8-135">Para adicionar redirecionamentos de associação a um arquivo Web. config:</span><span class="sxs-lookup"><span data-stu-id="374b8-135">To add binding redirects to a web.config file:</span></span>

1. <span data-ttu-id="374b8-136">No Visual Studio, compile o aplicativo e verifique a existência de avisos de compilação.</span><span class="sxs-lookup"><span data-stu-id="374b8-136">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="374b8-137">![Aviso para conflitos de referência de assembly de compilação](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="374b8-137">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="374b8-138">Se houver conflitos de associação de assembly, um aviso será exibido.</span><span class="sxs-lookup"><span data-stu-id="374b8-138">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="374b8-139">Clique duas vezes no aviso, ou selecione o aviso e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="374b8-139">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="374b8-140">Uma caixa de diálogo que permite adicionar automaticamente os redirecionamentos da associação necessários ao arquivo web.config de origem é exibida.</span><span class="sxs-lookup"><span data-stu-id="374b8-140">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>

   <span data-ttu-id="374b8-141">![Caixa de diálogo de permissão de redirecionamento de associação](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="374b8-141">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="374b8-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="374b8-142">See also</span></span>

- [<span data-ttu-id="374b8-143">\<bindingRedirect > elemento</span><span class="sxs-lookup"><span data-stu-id="374b8-143">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="374b8-144">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="374b8-144">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)

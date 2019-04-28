---
title: Habilitar ou desabilitar os redirecionamentos de associação geradas automaticamente
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: f646445d5fa4556646700bb5daf8ac859631da2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61880096"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="30491-102">Como: Habilitar e desabilitar o redirecionamento automático de associação</span><span class="sxs-lookup"><span data-stu-id="30491-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="30491-103">Quando você compila aplicativos no Visual Studio que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores, redirecionamentos de associação poderão ser automaticamente adicionadas ao arquivo de configuração de aplicativo para substituir a Unificação do assembly.</span><span class="sxs-lookup"><span data-stu-id="30491-103">When you compile apps in Visual Studio that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="30491-104">Redirecionamentos de associação serão adicionados se o seu aplicativo ou seus componentes fizerem referência a mais de uma versão do mesmo assembly, mesmo se você especificar manualmente redirecionamentos de associação no arquivo de configuração para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30491-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="30491-105">O recurso de redirecionamento de associação automático afeta os aplicativos da área de trabalho e aplicativos web que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ou uma versão posterior, embora o comportamento é ligeiramente diferente para um aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="30491-105">The automatic binding redirection feature affects desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="30491-106">Você pode habilitar o redirecionamento de associação automático se você tiver aplicativos existentes destinados a versões anteriores do .NET Framework, ou você pode desativar esse recurso se você quiser criar manualmente redirecionamentos de associação.</span><span class="sxs-lookup"><span data-stu-id="30491-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="30491-107">Desabilitar os redirecionamentos de associação automáticos em aplicativos da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="30491-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="30491-108">Redirecionamentos de associação automáticos são habilitados por padrão para aplicativos de desktop do Windows que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="30491-108">Automatic binding redirects are enabled by default for Windows desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="30491-109">Os redirecionamentos de associação são adicionados à configuração de saída (**App. config**) de arquivos quando o aplicativo é compilado e substituem a Unificação do assembly que pode ocorrer de outra forma.</span><span class="sxs-lookup"><span data-stu-id="30491-109">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="30491-110">O código-fonte **App. config** arquivo não é modificado.</span><span class="sxs-lookup"><span data-stu-id="30491-110">The source **app.config** file is not modified.</span></span> <span data-ttu-id="30491-111">Modificando o arquivo de projeto para o aplicativo ou desmarcar uma caixa de seleção nas propriedades do projeto no Visual Studio, você pode desativar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="30491-111">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="30491-112">Desabilitar por meio das propriedades do projeto</span><span class="sxs-lookup"><span data-stu-id="30491-112">Disable through project properties</span></span>

<span data-ttu-id="30491-113">Se você tiver o Visual Studio 2017 versão 15.7 ou posterior, você pode desativar com facilidade os redirecionamentos de associação geradas automaticamente nas páginas de propriedades do projeto.</span><span class="sxs-lookup"><span data-stu-id="30491-113">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="30491-114">Clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="30491-114">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="30491-115">Sobre o **aplicativo** página, desmarque a opção a **gerar automaticamente redirecionamentos de associação** opção.</span><span class="sxs-lookup"><span data-stu-id="30491-115">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="30491-116">Pressione **Ctrl**+**S** para salvar a alteração.</span><span class="sxs-lookup"><span data-stu-id="30491-116">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="30491-117">Desabilitar manualmente no arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="30491-117">Disable manually in the project file</span></span>

1. <span data-ttu-id="30491-118">Abra o arquivo de projeto para edição usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="30491-118">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="30491-119">No Visual Studio, selecione o projeto no **Gerenciador de soluções**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="30491-119">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="30491-120">No Explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abri-lo no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="30491-120">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="30491-121">No Visual Studio, no **Gerenciador de soluções**, clique com botão direito no projeto e escolha **descarregar projeto**.</span><span class="sxs-lookup"><span data-stu-id="30491-121">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="30491-122">Clique com botão direito do projeto descarregado novamente e, em seguida, escolha **Editar [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="30491-122">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="30491-123">No arquivo de projeto, localize a seguinte entrada de propriedade:</span><span class="sxs-lookup"><span data-stu-id="30491-123">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="30491-124">Altere `true` para `false`:</span><span class="sxs-lookup"><span data-stu-id="30491-124">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="30491-125">Habilitar redirecionamentos de associação automáticos manualmente</span><span class="sxs-lookup"><span data-stu-id="30491-125">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="30491-126">Você pode habilitar redirecionamentos de associação automáticos em aplicativos existentes destinados a versões anteriores do .NET Framework, ou em casos em que você é automaticamente solicitado a adicionar um redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="30491-126">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="30491-127">Se você estiver visando uma versão mais recente do framework, mas não solicitar automaticamente a adição de um redirecionamento, você provavelmente obterá saída de compilação que solicitará o remapeamento assemblies.</span><span class="sxs-lookup"><span data-stu-id="30491-127">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="30491-128">Abra o arquivo de projeto para edição usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="30491-128">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="30491-129">No Visual Studio, selecione o projeto no **Gerenciador de soluções**e, em seguida, escolha **Abrir pasta no Explorador de arquivos** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="30491-129">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="30491-130">No Explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abri-lo no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="30491-130">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="30491-131">No Visual Studio, no **Gerenciador de soluções**, clique com botão direito no projeto e escolha **descarregar projeto**.</span><span class="sxs-lookup"><span data-stu-id="30491-131">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="30491-132">Clique com botão direito do projeto descarregado novamente e, em seguida, escolha **Editar [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="30491-132">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="30491-133">Adicione o seguinte elemento ao primeiro grupo de propriedades de configuração (sob o \<PropertyGroup > marca):</span><span class="sxs-lookup"><span data-stu-id="30491-133">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="30491-134">A seguir mostra um exemplo de arquivo de projeto com o elemento inserido:</span><span class="sxs-lookup"><span data-stu-id="30491-134">The following shows an example project file with the element inserted:</span></span>

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

3. <span data-ttu-id="30491-135">Compile seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="30491-135">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="30491-136">Habilitar redirecionamentos de associação automáticos em aplicativos web</span><span class="sxs-lookup"><span data-stu-id="30491-136">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="30491-137">Redirecionamentos de associação automáticos são implementados de maneira diferente para aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="30491-137">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="30491-138">Porque a configuração de origem (**Web. config**) arquivo deve ser modificado para aplicativos web, redirecionamentos de associação não são automaticamente adicionados ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="30491-138">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="30491-139">Entretanto, o Visual Studio o notifica sobre conflitos de associação e você pode adicionar redirecionamentos de associação para resolver os conflitos.</span><span class="sxs-lookup"><span data-stu-id="30491-139">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="30491-140">Como sempre, você será solicitado a adicionar redirecionamentos de associação, você não precisa desabilitar explicitamente esse recurso para um aplicativo web.</span><span class="sxs-lookup"><span data-stu-id="30491-140">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="30491-141">Para adicionar redirecionamentos de associação para um **Web. config** arquivo:</span><span class="sxs-lookup"><span data-stu-id="30491-141">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="30491-142">No Visual Studio, compile o aplicativo e verifique a existência de avisos de compilação.</span><span class="sxs-lookup"><span data-stu-id="30491-142">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="30491-143">![Aviso para conflitos de referência de assembly de compilação](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="30491-143">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="30491-144">Se houver conflitos de associação de assembly, um aviso será exibido.</span><span class="sxs-lookup"><span data-stu-id="30491-144">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="30491-145">Clique duas vezes no aviso, ou selecione o aviso e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="30491-145">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="30491-146">Caixa de diálogo que permite que você adicione automaticamente a associação necessário redireciona para a fonte **Web. config** arquivo aparece.</span><span class="sxs-lookup"><span data-stu-id="30491-146">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="30491-147">![Caixa de diálogo de permissão de redirecionamento de associação](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="30491-147">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="30491-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30491-148">See also</span></span>

- [<span data-ttu-id="30491-149">\<bindingRedirect > elemento</span><span class="sxs-lookup"><span data-stu-id="30491-149">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="30491-150">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="30491-150">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)

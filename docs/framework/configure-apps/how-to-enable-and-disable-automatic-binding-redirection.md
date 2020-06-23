---
title: Habilitar ou desabilitar redirecionamentos de associação gerados automaticamente
description: Leia como habilitar ou desabilitar o redirecionamento de associação automática. Esse recurso afeta os aplicativos da área de trabalho e os aplicativos Web destinados ao .NET 4.5.1 ou posterior.
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: edee95f6c3b2c2d74c4f1b68e0a65e5cb0e85f54
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105391"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="6f1a6-104">Como: Habilitar e desabilitar o redirecionamento automático de associação</span><span class="sxs-lookup"><span data-stu-id="6f1a6-104">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="6f1a6-105">Quando você compila aplicativos no Visual Studio destinados ao .NET Framework 4.5.1 e versões posteriores, os redirecionamentos de associação podem ser adicionados automaticamente ao arquivo de configuração do aplicativo para substituir a unificação do assembly.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-105">When you compile apps in Visual Studio that target the .NET Framework 4.5.1 and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="6f1a6-106">Redirecionamentos de associação serão adicionados se o seu aplicativo ou seus componentes fizerem referência a mais de uma versão do mesmo assembly, mesmo se você especificar manualmente redirecionamentos de associação no arquivo de configuração para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-106">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="6f1a6-107">O recurso de redirecionamento de associação automática afeta aplicativos da área de trabalho e aplicativos Web direcionados para o .NET Framework 4.5.1 ou uma versão posterior, embora o comportamento seja um pouco diferente para um aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-107">The automatic binding redirection feature affects desktop apps and web apps that target the .NET Framework 4.5.1 or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="6f1a6-108">Você pode habilitar o redirecionamento de associação automática se tiver aplicativos que se destinam a versões anteriores do .NET Framework, ou pode desabilitar esse recurso se desejar criar manualmente os redirecionamentos de associação.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-108">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="6f1a6-109">Desabilitar redirecionamentos de associação automática em aplicativos da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="6f1a6-109">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="6f1a6-110">Os redirecionamentos de associação automática são habilitados por padrão para aplicativos de área de trabalho do Windows direcionados para o .NET Framework 4.5.1 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-110">Automatic binding redirects are enabled by default for Windows desktop apps that target the .NET Framework 4.5.1 and later versions.</span></span> <span data-ttu-id="6f1a6-111">Os redirecionamentos de associação são adicionados ao arquivo de configuração de saída (**app.config**) quando o aplicativo é compilado e substituem a Unificação de assembly que, de outra forma, poderia ocorrer.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-111">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="6f1a6-112">O arquivo de **app.config** de origem não é modificado.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-112">The source **app.config** file is not modified.</span></span> <span data-ttu-id="6f1a6-113">Você pode desabilitar esse recurso modificando o arquivo de projeto do aplicativo ou desmarcando uma caixa de seleção nas propriedades do projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-113">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="6f1a6-114">Desabilitar por meio de propriedades do projeto</span><span class="sxs-lookup"><span data-stu-id="6f1a6-114">Disable through project properties</span></span>

<span data-ttu-id="6f1a6-115">Se você tiver o Visual Studio 2017 versão 15,7 ou posterior, poderá desabilitar facilmente os redirecionamentos de associação gerados automaticamente nas páginas de propriedades do projeto.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-115">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="6f1a6-116">Clique com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-116">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="6f1a6-117">Na página do **aplicativo** , desmarque a opção **gerar redirecionamentos de associação automaticamente** .</span><span class="sxs-lookup"><span data-stu-id="6f1a6-117">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="6f1a6-118">Pressione **Ctrl** + **S** para salvar a alteração.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-118">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="6f1a6-119">Desabilitar manualmente no arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="6f1a6-119">Disable manually in the project file</span></span>

1. <span data-ttu-id="6f1a6-120">Abra o arquivo de projeto para edição usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="6f1a6-120">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="6f1a6-121">No Visual Studio, selecione o projeto em **Gerenciador de soluções**e, em seguida, escolha **abrir pasta no explorador de arquivos** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="6f1a6-122">No explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abra-o no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-122">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="6f1a6-123">No Visual Studio, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto e escolha **descarregar projeto**.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-123">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="6f1a6-124">Clique com o botão direito do mouse no projeto descarregado e escolha **Editar [ProjectName. csproj]**.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-124">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="6f1a6-125">No arquivo de projeto, localize a seguinte entrada de propriedade:</span><span class="sxs-lookup"><span data-stu-id="6f1a6-125">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="6f1a6-126">Altere `true` para `false`:</span><span class="sxs-lookup"><span data-stu-id="6f1a6-126">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="6f1a6-127">Habilitar redirecionamentos de associação automática manualmente</span><span class="sxs-lookup"><span data-stu-id="6f1a6-127">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="6f1a6-128">Você pode habilitar redirecionamentos de associação automática em aplicativos existentes direcionados a versões mais antigas do .NET Framework, ou em casos em que não seja solicitado automaticamente a adicionar um redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-128">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="6f1a6-129">Se você estiver direcionando para uma versão mais recente da estrutura, mas não for solicitado automaticamente a adicionar um redirecionamento, provavelmente obterá uma saída de compilação que sugere os assemblies de remapeamento.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-129">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="6f1a6-130">Abra o arquivo de projeto para edição usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="6f1a6-130">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="6f1a6-131">No Visual Studio, selecione o projeto em **Gerenciador de soluções**e, em seguida, escolha **abrir pasta no explorador de arquivos** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-131">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="6f1a6-132">No explorador de arquivos, localize o arquivo de projeto (. csproj ou. vbproj) e abra-o no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-132">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="6f1a6-133">No Visual Studio, em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto e escolha **descarregar projeto**.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-133">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="6f1a6-134">Clique com o botão direito do mouse no projeto descarregado e escolha **Editar [ProjectName. csproj]**.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-134">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="6f1a6-135">Adicione o seguinte elemento ao primeiro grupo de propriedades de configuração (sob a \<PropertyGroup> marca):</span><span class="sxs-lookup"><span data-stu-id="6f1a6-135">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="6f1a6-136">Veja a seguir um exemplo de arquivo de projeto com o elemento inserido:</span><span class="sxs-lookup"><span data-stu-id="6f1a6-136">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="6f1a6-137">Compile seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-137">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="6f1a6-138">Habilitar redirecionamentos de associação automática em aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="6f1a6-138">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="6f1a6-139">Redirecionamentos de associação automáticos são implementados de maneira diferente para aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-139">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="6f1a6-140">Como o arquivo de configuração de origem (**web.config**) deve ser modificado para aplicativos Web, os redirecionamentos de associação não são adicionados automaticamente ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-140">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="6f1a6-141">Entretanto, o Visual Studio o notifica sobre conflitos de associação e você pode adicionar redirecionamentos de associação para resolver os conflitos.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-141">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="6f1a6-142">Como você sempre é solicitado a adicionar redirecionamentos de associação, não é necessário desabilitar explicitamente esse recurso para um aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-142">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="6f1a6-143">Para adicionar redirecionamentos de associação a um arquivo de **web.config** :</span><span class="sxs-lookup"><span data-stu-id="6f1a6-143">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="6f1a6-144">No Visual Studio, compile o aplicativo e verifique a existência de avisos de compilação.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-144">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="6f1a6-145">![Aviso de compilação para conflitos de referência de assembly](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="6f1a6-145">![Build warning for assembly reference conflicts](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="6f1a6-146">Se houver conflitos de associação de assembly, um aviso será exibido.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-146">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="6f1a6-147">Clique duas vezes no aviso ou selecione o aviso e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-147">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="6f1a6-148">Uma caixa de diálogo que permite adicionar automaticamente os redirecionamentos de associação necessários para o arquivo de **web.config** de origem é exibida.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-148">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="6f1a6-149">![Diálogo de permissão de redirecionamento de associação](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="6f1a6-149">![Binding redirect permission dialog](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="6f1a6-150">Veja também</span><span class="sxs-lookup"><span data-stu-id="6f1a6-150">See also</span></span>

- [<span data-ttu-id="6f1a6-151">\<bindingRedirect>Elementos</span><span class="sxs-lookup"><span data-stu-id="6f1a6-151">\<bindingRedirect> Element</span></span>](./file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="6f1a6-152">Redirecionando versões de assembly</span><span class="sxs-lookup"><span data-stu-id="6f1a6-152">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)

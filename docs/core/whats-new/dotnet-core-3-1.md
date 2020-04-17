---
title: Novidades do .NET Core 3.1
description: Conheça os novos recursos encontrados no .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: b52615a3fb288a6ca0622deb83f4db3c8e3587fb
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607900"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="a8d2a-103">Novidades do .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="a8d2a-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="a8d2a-104">Este artigo descreve o que há de novo no .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="a8d2a-105">Esta versão contém pequenas melhorias no .NET Core 3.0, com foco em pequenas, mas importantes correções.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="a8d2a-106">A característica mais importante sobre o .NET Core 3.1 é que é uma versão [LTS (de suporte de longo prazo).](#long-term-support)</span><span class="sxs-lookup"><span data-stu-id="a8d2a-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="a8d2a-107">Se você estiver usando o Visual Studio 2019, você deve atualizar para o [Visual Studio 2019 versão 16.4 ou posterior](https://visualstudio.microsoft.com/downloads/) para trabalhar com projetos .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="a8d2a-108">Para obter informações sobre as novidades do Visual Studio versão 16.4, consulte [O que há de novo no Visual Studio 2019 versão 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="a8d2a-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="a8d2a-109">Visual Studio para Mac também suporta e inclui .NET Core 3.1 no Visual Studio para Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="a8d2a-110">Para obter mais informações sobre a versão, consulte o [anúncio do .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="a8d2a-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="a8d2a-111">[Baixe e comece com o .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) no Windows, macOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="a8d2a-112">Suporte de longo prazo</span><span class="sxs-lookup"><span data-stu-id="a8d2a-112">Long-term support</span></span>

<span data-ttu-id="a8d2a-113">.NET Core 3.1 é uma versão LTS com suporte da Microsoft para os próximos três anos.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="a8d2a-114">É altamente recomendável que você mova seus aplicativos para o .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="a8d2a-115">O ciclo de vida atual de outras grandes versões é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a8d2a-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="a8d2a-116">Versão</span><span class="sxs-lookup"><span data-stu-id="a8d2a-116">Release</span></span> | <span data-ttu-id="a8d2a-117">Observação</span><span class="sxs-lookup"><span data-stu-id="a8d2a-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="a8d2a-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a8d2a-118">.NET Core 3.0</span></span> | <span data-ttu-id="a8d2a-119">Fim da vida em 3 de março de 2020.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="a8d2a-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="a8d2a-120">.NET Core 2.2</span></span> | <span data-ttu-id="a8d2a-121">Fim da vida em 23 de dezembro de 2019.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="a8d2a-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a8d2a-122">.NET Core 2.1</span></span> | <span data-ttu-id="a8d2a-123">Fim da vida em 21 de agosto de 2021.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="a8d2a-124">Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="a8d2a-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="a8d2a-125">aplicativo macOSHost e autenticação em cartório</span><span class="sxs-lookup"><span data-stu-id="a8d2a-125">macOS appHost and notarization</span></span>

<span data-ttu-id="a8d2a-126">*somente para macOS*</span><span class="sxs-lookup"><span data-stu-id="a8d2a-126">*macOS only*</span></span>

<span data-ttu-id="a8d2a-127">Começando com o .NET Core SDK 3.1 autenticado para macOS, a configuração appHost é desativada por padrão.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="a8d2a-128">Para obter mais informações, consulte [macOS Catalina Notarization e o impacto em downloads e projetos do .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="a8d2a-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="a8d2a-129">Quando a configuração appHost está ativada, o .NET Core gera um executável Mach-O nativo quando você constrói ou publica.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="a8d2a-130">Seu aplicativo é executado no contexto do aplicativoHost quando `dotnet run` é executado a partir do código-fonte com o comando, ou iniciando o executável Mach-O diretamente.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="a8d2a-131">Sem o aplicativoHost, a única maneira de um usuário `dotnet <filename.dll>` iniciar um aplicativo dependente de tempo de [execução](../deploying/index.md#publish-runtime-dependent) é com o comando.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="a8d2a-132">Um aplicativoHost é sempre criado quando você publica seu aplicativo [independente](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="a8d2a-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="a8d2a-133">Você pode configurar o appHost no nível do projeto ou alternar `dotnet` o `-p:UseAppHost` aplicativoHost para um comando específico com o parâmetro:</span><span class="sxs-lookup"><span data-stu-id="a8d2a-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="a8d2a-134">Arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="a8d2a-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="a8d2a-135">Parâmetro de linha de comando</span><span class="sxs-lookup"><span data-stu-id="a8d2a-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="a8d2a-136">Para obter mais `UseAppHost` informações sobre a configuração, consulte [as propriedades MSBuild para Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="a8d2a-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="a8d2a-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8d2a-137">Windows Forms</span></span>

<span data-ttu-id="a8d2a-138">*Somente Windows*</span><span class="sxs-lookup"><span data-stu-id="a8d2a-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="a8d2a-139">Há mudanças quebrando nos Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="a8d2a-140">Os controles legados foram incluídos no Windows Forms que não estão disponíveis na caixa de ferramentas do Visual Studio Designer há algum tempo.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="a8d2a-141">Estes foram substituídos por novos controles de volta no Quadro .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="a8d2a-142">Estes foram removidos do SDK da área de trabalho para o .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="a8d2a-143">Controle removido</span><span class="sxs-lookup"><span data-stu-id="a8d2a-143">Removed control</span></span> | <span data-ttu-id="a8d2a-144">Substituição recomendada</span><span class="sxs-lookup"><span data-stu-id="a8d2a-144">Recommended replacement</span></span> | <span data-ttu-id="a8d2a-145">APIs associadas removidas</span><span class="sxs-lookup"><span data-stu-id="a8d2a-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="a8d2a-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="a8d2a-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="a8d2a-147">Datagridcell</span><span class="sxs-lookup"><span data-stu-id="a8d2a-147">DataGridCell</span></span><br/><span data-ttu-id="a8d2a-148">Datagridrow</span><span class="sxs-lookup"><span data-stu-id="a8d2a-148">DataGridRow</span></span><br/><span data-ttu-id="a8d2a-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="a8d2a-149">DataGridTableCollection</span></span><br/><span data-ttu-id="a8d2a-150">Datagridcolumncollection</span><span class="sxs-lookup"><span data-stu-id="a8d2a-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="a8d2a-151">Datagridtablestyle</span><span class="sxs-lookup"><span data-stu-id="a8d2a-151">DataGridTableStyle</span></span><br/><span data-ttu-id="a8d2a-152">Datagridcolumnstyle</span><span class="sxs-lookup"><span data-stu-id="a8d2a-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="a8d2a-153">Datagridlinestyle</span><span class="sxs-lookup"><span data-stu-id="a8d2a-153">DataGridLineStyle</span></span><br/><span data-ttu-id="a8d2a-154">DataGridParentRowsRótulo</span><span class="sxs-lookup"><span data-stu-id="a8d2a-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="a8d2a-155">Datagridparentrowslabelstyle</span><span class="sxs-lookup"><span data-stu-id="a8d2a-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="a8d2a-156">Datagridboolcolumn</span><span class="sxs-lookup"><span data-stu-id="a8d2a-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="a8d2a-157">Datagridtextbox</span><span class="sxs-lookup"><span data-stu-id="a8d2a-157">DataGridTextBox</span></span><br/><span data-ttu-id="a8d2a-158">Gridcolumnstylescollection</span><span class="sxs-lookup"><span data-stu-id="a8d2a-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="a8d2a-159">Gridtablestylescollection</span><span class="sxs-lookup"><span data-stu-id="a8d2a-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="a8d2a-160">Hittesttype</span><span class="sxs-lookup"><span data-stu-id="a8d2a-160">HitTestType</span></span> |
| <span data-ttu-id="a8d2a-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="a8d2a-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="a8d2a-162">Toolbarappearance</span><span class="sxs-lookup"><span data-stu-id="a8d2a-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="a8d2a-163">Toolbarbutton</span><span class="sxs-lookup"><span data-stu-id="a8d2a-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="a8d2a-164">Toolbarbuttonclickeventargs</span><span class="sxs-lookup"><span data-stu-id="a8d2a-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="a8d2a-165">Barra de ferramentasBotãoClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="a8d2a-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="a8d2a-166">Toolbarbuttonstyle</span><span class="sxs-lookup"><span data-stu-id="a8d2a-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="a8d2a-167">Toolbartextalign</span><span class="sxs-lookup"><span data-stu-id="a8d2a-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="a8d2a-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="a8d2a-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="a8d2a-169">Menuitemcollection</span><span class="sxs-lookup"><span data-stu-id="a8d2a-169">MenuItemCollection</span></span> |
| <span data-ttu-id="a8d2a-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="a8d2a-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="a8d2a-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="a8d2a-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="a8d2a-172">Recomendamos que atualize seus aplicativos para o .NET Core 3.1 e passe para os controles de substituição.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="a8d2a-173">Substituir os controles é um processo simples, essencialmente "encontrar e substituir" no tipo.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="a8d2a-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="a8d2a-174">C++/CLI</span></span>

<span data-ttu-id="a8d2a-175">*Somente Windows*</span><span class="sxs-lookup"><span data-stu-id="a8d2a-175">*Windows only*</span></span>

<span data-ttu-id="a8d2a-176">O suporte foi adicionado para a criação de projetos C++/CLI (também conhecidos como "C++") gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="a8d2a-177">Binários produzidos a partir desses projetos são compatíveis com as versões .NET Core 3.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="a8d2a-178">Para adicionar suporte para C++/CLI no Visual Studio 2019 versão 16.4, instale o desenvolvimento de [desktop com carga de trabalho C++.](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)</span><span class="sxs-lookup"><span data-stu-id="a8d2a-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="a8d2a-179">Esta carga de trabalho adiciona dois modelos ao Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="a8d2a-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="a8d2a-180">Biblioteca de classes CLR (núcleo.NET)</span><span class="sxs-lookup"><span data-stu-id="a8d2a-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="a8d2a-181">Projeto vazio CLR (núcleo.NET)</span><span class="sxs-lookup"><span data-stu-id="a8d2a-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="a8d2a-182">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a8d2a-182">Next steps</span></span>

- [<span data-ttu-id="a8d2a-183">Revise as alterações de quebra entre o Núcleo .NET 3.0 e o 3.1.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="a8d2a-184">Revise as alterações de quebra no .NET Core 3.1 para aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a8d2a-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)

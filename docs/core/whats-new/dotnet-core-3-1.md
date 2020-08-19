---
title: Novidades do .NET Core 3.1
description: Saiba mais sobre os novos recursos encontrados no .NET Core 3,1.
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 42d4f7e8800bf2d13d584084f8a41bad2ada534f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608121"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="ddaeb-103">Novidades do .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ddaeb-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="ddaeb-104">Este artigo descreve o que há de novo no .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="ddaeb-105">Esta versão contém pequenas melhorias no .NET Core 3,0, concentrando-se em correções pequenas, mas importantes.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="ddaeb-106">O recurso mais importante sobre o .NET Core 3,1 é que ele é uma versão de [LTS (suporte a longo prazo)](#long-term-support) .</span><span class="sxs-lookup"><span data-stu-id="ddaeb-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="ddaeb-107">Se você estiver usando o Visual Studio 2019, deverá atualizar para o [visual studio 2019 versão 16,4 ou posterior](https://visualstudio.microsoft.com/downloads/) para trabalhar com projetos do .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="ddaeb-108">Para obter informações sobre as novidades do Visual Studio versão 16,4, consulte [What ' s New in Visual studio 2019 versão 16,4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="ddaeb-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="ddaeb-109">O Visual Studio para Mac também dá suporte a e inclui o .NET Core 3,1 no Visual Studio para Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="ddaeb-110">Para obter mais informações sobre a versão, consulte o [anúncio do .NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="ddaeb-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="ddaeb-111">[Baixe e comece a usar o .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) no Windows, no MacOS ou no Linux.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="ddaeb-112">Suporte de longo prazo</span><span class="sxs-lookup"><span data-stu-id="ddaeb-112">Long-term support</span></span>

<span data-ttu-id="ddaeb-113">O .NET Core 3,1 é uma versão LTS com suporte da Microsoft nos próximos três anos.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="ddaeb-114">É altamente recomendável que você mova seus aplicativos para o .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="ddaeb-115">O ciclo de vida atual de outras versões principais é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ddaeb-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="ddaeb-116">Versão</span><span class="sxs-lookup"><span data-stu-id="ddaeb-116">Release</span></span> | <span data-ttu-id="ddaeb-117">Observação</span><span class="sxs-lookup"><span data-stu-id="ddaeb-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="ddaeb-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ddaeb-118">.NET Core 3.0</span></span> | <span data-ttu-id="ddaeb-119">Fim da vida útil em 3 de março de 2020.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="ddaeb-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ddaeb-120">.NET Core 2.2</span></span> | <span data-ttu-id="ddaeb-121">Fim da vida útil em 23 de dezembro de 2019.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="ddaeb-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ddaeb-122">.NET Core 2.1</span></span> | <span data-ttu-id="ddaeb-123">Fim da vida útil em 21 de agosto de 2021.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="ddaeb-124">Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="ddaeb-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="ddaeb-125">macOS appHost e notarization</span><span class="sxs-lookup"><span data-stu-id="ddaeb-125">macOS appHost and notarization</span></span>

<span data-ttu-id="ddaeb-126">*somente macOS*</span><span class="sxs-lookup"><span data-stu-id="ddaeb-126">*macOS only*</span></span>

<span data-ttu-id="ddaeb-127">A partir do notarized SDK do .NET Core 3,1 para macOS, a configuração appHost é desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="ddaeb-128">Para obter mais informações, consulte [o notarization Catalina do MacOS e o impacto sobre os downloads e projetos do .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="ddaeb-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="ddaeb-129">Quando a configuração appHost está habilitada, o .NET Core gera um executável de Mach-O nativo quando você cria ou publica.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="ddaeb-130">Seu aplicativo é executado no contexto do appHost quando ele é executado do código-fonte com o `dotnet run` comando ou iniciando o executável de Mach-o diretamente.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="ddaeb-131">Sem o appHost, a única maneira como um usuário pode iniciar um aplicativo [dependente da estrutura](../deploying/index.md#publish-framework-dependent) é com o `dotnet <filename.dll>` comando.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-131">Without the appHost, the only way a user can start a [framework-dependent](../deploying/index.md#publish-framework-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="ddaeb-132">Um appHost é sempre criado quando você publica [seu aplicativo independente](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="ddaeb-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="ddaeb-133">Você pode configurar o appHost no nível do projeto ou alternar o appHost para um `dotnet` comando específico com o `-p:UseAppHost` parâmetro:</span><span class="sxs-lookup"><span data-stu-id="ddaeb-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="ddaeb-134">Arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="ddaeb-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="ddaeb-135">Parâmetro de linha de comando</span><span class="sxs-lookup"><span data-stu-id="ddaeb-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="ddaeb-136">Para obter mais informações sobre a `UseAppHost` configuração, consulte [Propriedades do MSBuild para Microsoft. net. SDK](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="ddaeb-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="ddaeb-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ddaeb-137">Windows Forms</span></span>

<span data-ttu-id="ddaeb-138">*Somente Windows*</span><span class="sxs-lookup"><span data-stu-id="ddaeb-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="ddaeb-139">Há alterações significativas no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="ddaeb-140">Os controles herdados foram incluídos em Windows Forms que não estão disponíveis na caixa de ferramentas do Visual Studio designer por algum tempo.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="ddaeb-141">Eles foram substituídos por novos controles de volta no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="ddaeb-142">Elas foram removidas do SDK de desktop para .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="ddaeb-143">Controle removido</span><span class="sxs-lookup"><span data-stu-id="ddaeb-143">Removed control</span></span> | <span data-ttu-id="ddaeb-144">Substituição recomendada</span><span class="sxs-lookup"><span data-stu-id="ddaeb-144">Recommended replacement</span></span> | <span data-ttu-id="ddaeb-145">APIs associadas removidas</span><span class="sxs-lookup"><span data-stu-id="ddaeb-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="ddaeb-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="ddaeb-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="ddaeb-147">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="ddaeb-147">DataGridCell</span></span><br/><span data-ttu-id="ddaeb-148">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="ddaeb-148">DataGridRow</span></span><br/><span data-ttu-id="ddaeb-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="ddaeb-149">DataGridTableCollection</span></span><br/><span data-ttu-id="ddaeb-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="ddaeb-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="ddaeb-151">DataGridTableStyle</span><span class="sxs-lookup"><span data-stu-id="ddaeb-151">DataGridTableStyle</span></span><br/><span data-ttu-id="ddaeb-152">DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="ddaeb-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="ddaeb-153">Datagridlinesstyle</span><span class="sxs-lookup"><span data-stu-id="ddaeb-153">DataGridLineStyle</span></span><br/><span data-ttu-id="ddaeb-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="ddaeb-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="ddaeb-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="ddaeb-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="ddaeb-156">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="ddaeb-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="ddaeb-157">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="ddaeb-157">DataGridTextBox</span></span><br/><span data-ttu-id="ddaeb-158">GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="ddaeb-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="ddaeb-159">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="ddaeb-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="ddaeb-160">HitTesttype</span><span class="sxs-lookup"><span data-stu-id="ddaeb-160">HitTestType</span></span> |
| <span data-ttu-id="ddaeb-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="ddaeb-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="ddaeb-162">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="ddaeb-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="ddaeb-163">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="ddaeb-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="ddaeb-164">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="ddaeb-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="ddaeb-165">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="ddaeb-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="ddaeb-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="ddaeb-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="ddaeb-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="ddaeb-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="ddaeb-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="ddaeb-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="ddaeb-169">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="ddaeb-169">MenuItemCollection</span></span> |
| <span data-ttu-id="ddaeb-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="ddaeb-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="ddaeb-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="ddaeb-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="ddaeb-172">Recomendamos que você atualize seus aplicativos para o .NET Core 3,1 e vá para os controles de substituição.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="ddaeb-173">Substituir os controles é um processo simples, essencialmente "localizar e substituir" no tipo.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="ddaeb-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="ddaeb-174">C++/CLI</span></span>

<span data-ttu-id="ddaeb-175">*Somente Windows*</span><span class="sxs-lookup"><span data-stu-id="ddaeb-175">*Windows only*</span></span>

<span data-ttu-id="ddaeb-176">Foi adicionado suporte para a criação de projetos C++/CLI (também conhecidos como "C++ gerenciado").</span><span class="sxs-lookup"><span data-stu-id="ddaeb-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="ddaeb-177">Os binários produzidos a partir desses projetos são compatíveis com o .NET Core 3,0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="ddaeb-178">Para adicionar suporte para C++/CLI no Visual Studio 2019 versão 16,4, instale o [desenvolvimento de desktop com carga de trabalho do C++](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span><span class="sxs-lookup"><span data-stu-id="ddaeb-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="ddaeb-179">Essa carga de trabalho adiciona dois modelos ao Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="ddaeb-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="ddaeb-180">Biblioteca de classes CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="ddaeb-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="ddaeb-181">Projeto CLR vazio (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="ddaeb-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="ddaeb-182">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ddaeb-182">Next steps</span></span>

- [<span data-ttu-id="ddaeb-183">Examine as alterações significativas entre o .NET Core 3,0 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="ddaeb-184">Examine as alterações significativas no .NET Core 3,1 para aplicativos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ddaeb-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)

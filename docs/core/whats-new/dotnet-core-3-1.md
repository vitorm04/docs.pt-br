---
title: Novidades do .NET Core 3.1
description: Saiba mais sobre os novos recursos encontrados no .NET Core 3,1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156550"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="db2fa-103">Novidades do .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="db2fa-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="db2fa-104">Este artigo descreve o que há de novo no .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="db2fa-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="db2fa-105">Esta versão contém pequenas melhorias no .NET Core 3,0, concentrando-se em correções pequenas, mas importantes.</span><span class="sxs-lookup"><span data-stu-id="db2fa-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="db2fa-106">O recurso mais importante sobre o .NET Core 3,1 é que ele é uma versão de [LTS (suporte a longo prazo)](#long-term-support) .</span><span class="sxs-lookup"><span data-stu-id="db2fa-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="db2fa-107">Se você estiver usando o Visual Studio 2019, deverá atualizar para o [visual studio 2019 versão 16,4](https://visualstudio.microsoft.com/downloads/) para trabalhar com projetos do .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="db2fa-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="db2fa-108">Para obter mais informações sobre as novidades do Visual Studio, consulte [What ' s New in Visual studio 2019 versão 16,4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="db2fa-108">For more information on what's new in Visual Studio, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="db2fa-109">O Visual Studio para Mac também dá suporte a e inclui o .NET Core 3,1 no Visual Studio para Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="db2fa-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="db2fa-110">Para obter mais informações sobre a versão, consulte o [anúncio do .NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="db2fa-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="db2fa-111">[Baixe e comece a usar o .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) no Windows, no MacOS ou no Linux.</span><span class="sxs-lookup"><span data-stu-id="db2fa-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="db2fa-112">Suporte de longo prazo</span><span class="sxs-lookup"><span data-stu-id="db2fa-112">Long-term support</span></span>

<span data-ttu-id="db2fa-113">O .NET Core 3,1 é uma versão LTS com suporte da Microsoft nos próximos três anos.</span><span class="sxs-lookup"><span data-stu-id="db2fa-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="db2fa-114">É altamente recomendável que você mova seus aplicativos para o .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="db2fa-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="db2fa-115">O ciclo de vida atual de outras versões principais é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="db2fa-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="db2fa-116">Versão</span><span class="sxs-lookup"><span data-stu-id="db2fa-116">Release</span></span> | <span data-ttu-id="db2fa-117">Observação</span><span class="sxs-lookup"><span data-stu-id="db2fa-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="db2fa-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="db2fa-118">.NET Core 3.0</span></span> | <span data-ttu-id="db2fa-119">Fim da vida útil em 3 de março de 2020.</span><span class="sxs-lookup"><span data-stu-id="db2fa-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="db2fa-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="db2fa-120">.NET Core 2.2</span></span> | <span data-ttu-id="db2fa-121">Fim da vida útil em 23 de dezembro de 2019.</span><span class="sxs-lookup"><span data-stu-id="db2fa-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="db2fa-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="db2fa-122">.NET Core 2.1</span></span> | <span data-ttu-id="db2fa-123">Fim da vida útil em 21 de agosto de 2021.</span><span class="sxs-lookup"><span data-stu-id="db2fa-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="db2fa-124">Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="db2fa-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="db2fa-125">macOS appHost e notarization</span><span class="sxs-lookup"><span data-stu-id="db2fa-125">macOS appHost and notarization</span></span>

<span data-ttu-id="db2fa-126">*somente macOS*</span><span class="sxs-lookup"><span data-stu-id="db2fa-126">*macOS only*</span></span>

<span data-ttu-id="db2fa-127">A partir do notarized SDK do .NET Core 3,1 para macOS, a configuração appHost é desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="db2fa-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="db2fa-128">Para obter mais informações, consulte [o notarization Catalina do MacOS e o impacto sobre os downloads e projetos do .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="db2fa-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="db2fa-129">Quando a configuração appHost está habilitada, o .NET Core gera um executável de Mach-O nativo quando você cria ou publica.</span><span class="sxs-lookup"><span data-stu-id="db2fa-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="db2fa-130">Seu aplicativo é executado no contexto do appHost quando ele é executado do código-fonte com o comando `dotnet run` ou iniciando o executável de Mach-O diretamente.</span><span class="sxs-lookup"><span data-stu-id="db2fa-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="db2fa-131">Sem o appHost, a única maneira como um usuário pode iniciar um aplicativo [dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) é com o comando `dotnet <filename.dll>`.</span><span class="sxs-lookup"><span data-stu-id="db2fa-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="db2fa-132">Um appHost é sempre criado quando você publica [seu aplicativo independente](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="db2fa-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="db2fa-133">Você pode configurar o appHost no nível do projeto ou alternar o appHost para um comando `dotnet` específico com o parâmetro `-p:UseAppHost`:</span><span class="sxs-lookup"><span data-stu-id="db2fa-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="db2fa-134">Arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="db2fa-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="db2fa-135">Parâmetro de linha de comando</span><span class="sxs-lookup"><span data-stu-id="db2fa-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="db2fa-136">Para obter mais informações sobre a configuração de `UseAppHost`, consulte [Propriedades do MSBuild para Microsoft. net. SDK](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="db2fa-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="db2fa-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db2fa-137">Windows Forms</span></span>

<span data-ttu-id="db2fa-138">*Somente Windows*</span><span class="sxs-lookup"><span data-stu-id="db2fa-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="db2fa-139">Há alterações significativas no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="db2fa-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="db2fa-140">Os controles herdados foram incluídos em Windows Forms que não estão disponíveis na caixa de ferramentas do Visual Studio designer por algum tempo.</span><span class="sxs-lookup"><span data-stu-id="db2fa-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="db2fa-141">Eles foram substituídos por novos controles de volta no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="db2fa-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="db2fa-142">Elas foram removidas do SDK de desktop para .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="db2fa-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="db2fa-143">Controle removido</span><span class="sxs-lookup"><span data-stu-id="db2fa-143">Removed control</span></span> | <span data-ttu-id="db2fa-144">Substituição recomendada</span><span class="sxs-lookup"><span data-stu-id="db2fa-144">Recommended replacement</span></span> | <span data-ttu-id="db2fa-145">APIs associadas removidas</span><span class="sxs-lookup"><span data-stu-id="db2fa-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="db2fa-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="db2fa-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="db2fa-147">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="db2fa-147">DataGridCell</span></span><br/><span data-ttu-id="db2fa-148">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="db2fa-148">DataGridRow</span></span><br/><span data-ttu-id="db2fa-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="db2fa-149">DataGridTableCollection</span></span><br/><span data-ttu-id="db2fa-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="db2fa-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="db2fa-151">DataGridTableStyle</span><span class="sxs-lookup"><span data-stu-id="db2fa-151">DataGridTableStyle</span></span><br/><span data-ttu-id="db2fa-152">DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="db2fa-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="db2fa-153">Datagridlinesstyle</span><span class="sxs-lookup"><span data-stu-id="db2fa-153">DataGridLineStyle</span></span><br/><span data-ttu-id="db2fa-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="db2fa-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="db2fa-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="db2fa-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="db2fa-156">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="db2fa-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="db2fa-157">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="db2fa-157">DataGridTextBox</span></span><br/><span data-ttu-id="db2fa-158">GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="db2fa-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="db2fa-159">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="db2fa-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="db2fa-160">HitTesttype</span><span class="sxs-lookup"><span data-stu-id="db2fa-160">HitTestType</span></span> |
| <span data-ttu-id="db2fa-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="db2fa-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="db2fa-162">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="db2fa-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="db2fa-163">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="db2fa-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="db2fa-164">ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="db2fa-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="db2fa-165">ToolBarButtonClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="db2fa-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="db2fa-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="db2fa-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="db2fa-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="db2fa-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="db2fa-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="db2fa-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="db2fa-169">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="db2fa-169">MenuItemCollection</span></span> |
| <span data-ttu-id="db2fa-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="db2fa-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="db2fa-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="db2fa-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="db2fa-172">Recomendamos que você atualize seus aplicativos para o .NET Core 3,1 e vá para os controles de substituição.</span><span class="sxs-lookup"><span data-stu-id="db2fa-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="db2fa-173">Substituir os controles é um processo simples, essencialmente "localizar e substituir" no tipo.</span><span class="sxs-lookup"><span data-stu-id="db2fa-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="db2fa-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="db2fa-174">C++/CLI</span></span>

<span data-ttu-id="db2fa-175">*Somente Windows*</span><span class="sxs-lookup"><span data-stu-id="db2fa-175">*Windows only*</span></span>

<span data-ttu-id="db2fa-176">Foi adicionado suporte para a criação C++de projetos/CLI (também conhecidos como C++"gerenciados").</span><span class="sxs-lookup"><span data-stu-id="db2fa-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="db2fa-177">Os binários produzidos a partir desses projetos são compatíveis com o .NET Core 3,0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="db2fa-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="db2fa-178">Para adicionar suporte a C++/CLI no Visual Studio 2019 versão 16,4, instale o [desenvolvimento de desktop C++ com carga de trabalho](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span><span class="sxs-lookup"><span data-stu-id="db2fa-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="db2fa-179">Essa carga de trabalho adiciona dois modelos ao Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="db2fa-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="db2fa-180">Biblioteca de classes CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="db2fa-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="db2fa-181">Projeto CLR vazio (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="db2fa-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="db2fa-182">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="db2fa-182">Next steps</span></span>

- [<span data-ttu-id="db2fa-183">Examine as alterações significativas entre o .NET Core 3,0 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="db2fa-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="db2fa-184">Examine as alterações significativas no .NET Core 3,1 para aplicativos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="db2fa-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)

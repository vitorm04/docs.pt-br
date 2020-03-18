---
title: Novidades do .NET Core 3.1
description: Conheça os novos recursos encontrados no .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156550"
---
# <a name="whats-new-in-net-core-31"></a>Novidades do .NET Core 3.1

Este artigo descreve o que há de novo no .NET Core 3.1. Esta versão contém pequenas melhorias no .NET Core 3.0, com foco em pequenas, mas importantes correções. A característica mais importante sobre o .NET Core 3.1 é que é uma versão [LTS (de suporte de longo prazo).](#long-term-support)

Se você estiver usando o Visual Studio 2019, você deve atualizar para o [Visual Studio 2019 versão 16.4](https://visualstudio.microsoft.com/downloads/) para trabalhar com projetos .NET Core 3.1. Para obter mais informações sobre as novidades do Visual Studio, veja [as novidades do Visual Studio 2019 versão 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).

Visual Studio para Mac também suporta e inclui .NET Core 3.1 no Visual Studio para Mac 8.4.

Para obter mais informações sobre a versão, consulte o [anúncio do .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Baixe e comece com o .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) no Windows, macOS ou Linux.

## <a name="long-term-support"></a>Suporte de longo prazo

.NET Core 3.1 é uma versão LTS com suporte da Microsoft para os próximos três anos. É altamente recomendável que você mova seus aplicativos para o .NET Core 3.1. O ciclo de vida atual de outras grandes versões é o seguinte:

| Versão | Observação |
| ------- | ---- |
| .NET Core 3.0 | Fim da vida em 3 de março de 2020.     |
| .NET Core 2.2 | Fim da vida em 23 de dezembro de 2019. |
| .NET Core 2.1 | Fim da vida em 21 de agosto de 2021.    |

Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="macos-apphost-and-notarization"></a>aplicativo macOSHost e autenticação em cartório

*somente para macOS*

Começando com o .NET Core SDK 3.1 autenticado para macOS, a configuração appHost é desativada por padrão. Para obter mais informações, consulte [macOS Catalina Notarization e o impacto em downloads e projetos do .NET Core](../install/macos-notarization-issues.md).

Quando a configuração appHost está ativada, o .NET Core gera um executável Mach-O nativo quando você constrói ou publica. Seu aplicativo é executado no contexto do aplicativoHost quando `dotnet run` é executado a partir do código-fonte com o comando, ou iniciando o executável Mach-O diretamente.

Sem o aplicativoHost, a única maneira de um usuário `dotnet <filename.dll>` iniciar um aplicativo dependente de tempo de [execução](../deploying/index.md#publish-runtime-dependent) é com o comando. Um aplicativoHost é sempre criado quando você publica seu aplicativo [independente](../deploying/index.md#publish-self-contained).

Você pode configurar o appHost no nível do projeto ou alternar `dotnet` o `-p:UseAppHost` aplicativoHost para um comando específico com o parâmetro:

- Arquivo de projeto

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Parâmetro de linha de comando

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Para obter mais `UseAppHost` informações sobre a configuração, consulte [as propriedades MSBuild para Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

## <a name="windows-forms"></a>Windows Forms

*Somente Windows*

> [!WARNING]
> Há mudanças quebrando nos Formulários do Windows.

Os controles legados foram incluídos no Windows Forms que não estão disponíveis na caixa de ferramentas do Visual Studio Designer há algum tempo. Estes foram substituídos por novos controles de volta no Quadro .NET 2.0. Estes foram removidos do SDK da área de trabalho para o .NET Core 3.1.

| Controle removido | Substituição recomendada | APIs associadas removidas |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | Datagridcell<br/>Datagridrow<br/>DataGridTableCollection<br/>Datagridcolumncollection<br/>Datagridtablestyle<br/>Datagridcolumnstyle<br/>Datagridlinestyle<br/>DataGridParentRowsRótulo<br/>Datagridparentrowslabelstyle<br/>Datagridboolcolumn<br/>Datagridtextbox<br/>Gridcolumnstylescollection<br/>Gridtablestylescollection<br/>Hittesttype |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | Toolbarappearance |
| Toolbarbutton   | <xref:System.Windows.Forms.ToolStripButton>   | Toolbarbuttonclickeventargs<br/>Barra de ferramentasBotãoClickEventHandler<br/>Toolbarbuttonstyle<br/>Toolbartextalign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | Menuitemcollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Recomendamos que atualize seus aplicativos para o .NET Core 3.1 e passe para os controles de substituição. Substituir os controles é um processo simples, essencialmente "encontrar e substituir" no tipo.

## <a name="ccli"></a>C++/CLI

*Somente Windows*

O suporte foi adicionado para a criação de projetos C++/CLI (também conhecidos como "C++") gerenciados. Binários produzidos a partir desses projetos são compatíveis com as versões .NET Core 3.0 e posteriores.

Para adicionar suporte para C++/CLI no Visual Studio 2019 versão 16.4, instale o desenvolvimento de [desktop com carga de trabalho C++.](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads) Esta carga de trabalho adiciona dois modelos ao Visual Studio:

- Biblioteca de classes CLR (núcleo.NET)
- Projeto vazio CLR (núcleo.NET)

## <a name="next-steps"></a>Próximas etapas

- [Revise as alterações de quebra entre o Núcleo .NET 3.0 e o 3.1.](../compatibility/3.0-3.1.md)
- [Revise as alterações de quebra no .NET Core 3.1 para aplicativos do Windows Forms.](../compatibility/winforms.md#net-core-31)

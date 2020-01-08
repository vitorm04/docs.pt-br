---
title: Novidades do .NET Core 3.1
description: Saiba mais sobre os novos recursos encontrados no .NET Core 3,1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a9f47c2909375251460b45792822e491d56fb242
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342859"
---
# <a name="whats-new-in-net-core-31"></a>Novidades do .NET Core 3.1

Este artigo descreve o que há de novo no .NET Core 3,1. Esta versão contém pequenas melhorias no .NET Core 3,0, concentrando-se em correções pequenas, mas importantes. O recurso mais importante sobre o .NET Core 3,1 é que ele é uma versão de [LTS (suporte a longo prazo)](#long-term-support) .

Se você estiver usando o Visual Studio 2019, deverá atualizar para o [visual studio 2019 versão 16,4](https://visualstudio.microsoft.com/downloads/) para trabalhar com projetos do .net Core 3,1. Para obter mais informações sobre o que há de novo no Visual Studio, consulte o [blog do Visual Studio](https://devblogs.microsoft.com/visualstudio/tis-the-season-visual-studio-2019/).

O Visual Studio para Mac também dá suporte e inclui o .NET Core 3,1, no canal de visualização Visual Studio para Mac 8,4. Você precisará optar pelo canal de visualização para usar o .NET Core 3,1.

Para obter mais informações sobre a versão, consulte o [anúncio do .NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Baixe e comece a usar o .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) no Windows, no MacOS ou no Linux.

## <a name="long-term-support"></a>Suporte de longo prazo

O .NET Core 3,1 é uma versão LTS com suporte da Microsoft nos próximos três anos. É altamente recomendável que você mova seus aplicativos para o .NET Core 3,1. O ciclo de vida atual de outras versões principais é o seguinte:

| Versão | Observação |
| ------- | ---- |
| .NET Core 3.0 | Fim da vida útil em 3 de março de 2020.     |
| .NET Core 2.2 | Fim da vida útil em 23 de dezembro de 2019. |
| .NET Core 2.1 | Fim da vida útil em 21 de agosto de 2021.    |

Para obter mais informações, consulte a [política de suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="windows-forms"></a>Windows Forms

*Somente Windows*

> [!WARNING]
> Há alterações significativas no Windows Forms.

Os controles herdados foram incluídos em Windows Forms que não estão disponíveis na caixa de ferramentas do Visual Studio designer por algum tempo. Eles foram substituídos por novos controles de volta no .NET Framework 2,0. Elas foram removidas do SDK de desktop para .NET Core 3,1.

| Controle removido | Substituição recomendada | APIs associadas removidas |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | DataGridCell<br/>DataGridRow<br/>DataGridTableCollection<br/>DataGridColumnCollection<br/>DataGridTableStyle<br/>DataGridColumnStyle<br/>Datagridlinesstyle<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>DataGridBoolColumn<br/>DataGridTextBox<br/>GridColumnStylesCollection<br/>GridTableStylesCollection<br/>HitTesttype |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | ToolBarAppearance |
| ToolBarButton   | <xref:System.Windows.Forms.ToolStripButton>   | ToolBarButtonClickEventArgs<br/>ToolBarButtonClickEventHandler<br/>ToolBarButtonStyle<br/>ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | MenuItemCollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Recomendamos que você atualize seus aplicativos para o .NET Core 3,1 e vá para os controles de substituição. Substituir os controles é um processo simples, essencialmente "localizar e substituir" no tipo.

## <a name="ccli"></a>C++/CLI

*Somente Windows*

Foi adicionado suporte para a criação C++de projetos/CLI (também conhecidos como C++"gerenciados"). Os binários produzidos a partir desses projetos são compatíveis com o .NET Core 3,0 e versões posteriores.

Para adicionar suporte a C++/CLI no Visual Studio 2019 16,4, instale o [desenvolvimento de desktop C++ com carga de trabalho](https://docs.microsoft.com/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads). Essa carga de trabalho adiciona dois modelos ao Visual Studio:

- Biblioteca de classes CLR (.NET Core)
- Projeto CLR vazio (.NET Core)

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

- [Examine as alterações significativas entre o .NET Core 3,0 e 3,1.](../compatibility/3.0-3.1.md)
- [Examine as alterações significativas entre .NET Framework e o .NET Core 3,0 para aplicativos Windows Forms.](../porting/winforms-breaking-changes.md)

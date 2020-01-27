---
title: Visão geral do componente OpenFileDialog
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728443"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>Visão geral do componente OpenFileDialog (Windows Forms)

O Windows Forms <xref:System.Windows.Forms.OpenFileDialog> componente é uma caixa de diálogo pré-configurada. É a mesma caixa de diálogo **Abrir arquivo** exposta pelo sistema operacional Windows. Ele é herdado da classe <xref:System.Windows.Forms.CommonDialog>.

## <a name="use-this-component"></a>Usar este componente

Use esse componente em seu aplicativo baseado no Windows como uma solução simples para seleção de arquivos em vez de configurar sua própria caixa de diálogo. Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários. No entanto, lembre-se de que, ao usar o componente <xref:System.Windows.Forms.OpenFileDialog>, você deve escrever sua própria lógica de abertura de arquivo.

Use o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo em tempo de execução. Você pode permitir que os usuários selecionem vários arquivos para serem abertos com a propriedade <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>. Além disso, você pode usar a propriedade <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> para determinar se uma caixa de seleção somente leitura aparece na caixa de diálogo. A propriedade <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> indica se a caixa de seleção somente leitura está selecionada. Por fim, a propriedade <xref:System.Windows.Forms.FileDialog.Filter%2A> define a cadeia de caracteres de filtro de nome de arquivo atual, que determina as opções que aparecem na caixa "arquivos do tipo" na caixa de diálogo.

Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.OpenFileDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.OpenFileDialog>
- [Componente OpenFileDialog](openfiledialog-component-windows-forms.md)

---
title: Visão geral do componente SaveFileDialog
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743106"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>Visão geral do componente SaveFileDialog (Windows Forms)

O Windows Forms <xref:System.Windows.Forms.SaveFileDialog> componente é uma caixa de diálogo pré-configurada. É o mesmo que a caixa de diálogo **salvar arquivo** padrão usada pelo Windows. Ele é herdado da classe <xref:System.Windows.Forms.CommonDialog>.

## <a name="working-with-the-savefiledialog-component"></a>Trabalhando com o componente SaveFileDialog

Use-o como uma solução simples para permitir que os usuários salvem arquivos em vez de configurar sua própria caixa de diálogo. Ao confiar nas caixas de diálogo padrão do Windows, a funcionalidade básica dos aplicativos que você cria é imediatamente familiar para os usuários. No entanto, lembre-se de que, ao usar o componente <xref:System.Windows.Forms.SaveFileDialog>, você deve escrever sua própria lógica de salvamento de arquivos.

Você pode usar o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo em tempo de execução. Você pode abrir um arquivo no modo de leitura/gravação usando o método <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>.

Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.SaveFileDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.SaveFileDialog>
- [Componente SaveFileDialog](savefiledialog-component-windows-forms.md)

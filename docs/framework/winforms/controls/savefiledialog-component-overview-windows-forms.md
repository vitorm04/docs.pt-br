---
title: Visão geral do componente SaveFileDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: b06c4d510cefdc7558944995594fd209b6121cb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103032"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>Visão geral do componente SaveFileDialog (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.SaveFileDialog> componente é uma caixa de diálogo pré-configurada. É o mesmo que o padrão **salvar arquivo** caixa de diálogo usada pelo Windows. Ele herda o <xref:System.Windows.Forms.CommonDialog> classe.  
  
## <a name="working-with-the-savefiledialog-component"></a>Trabalhando com o componente SaveFileDialog  
 Usá-lo como uma solução simples para habilitar os usuários salvem arquivos em vez de configurar sua própria caixa de diálogo. Confiando nas caixas de diálogo padrão do Windows, a funcionalidade básica de aplicativos que você criou é imediatamente familiar aos usuários. Lembre-se, no entanto, que, quando usar o <xref:System.Windows.Forms.SaveFileDialog> componente, você deve escrever sua própria lógica de salvamento do arquivo.  
  
 Você pode usar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução. Você pode abrir um arquivo no modo de leitura/gravação usando o <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> método.  
  
 Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.SaveFileDialog> componente aparece na bandeja na parte inferior do Designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.SaveFileDialog>
- [Componente SaveFileDialog](savefiledialog-component-windows-forms.md)

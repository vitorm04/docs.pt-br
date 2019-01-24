---
title: Visão geral do componente SaveFileDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: ab8eb5409d017c6ea73a44e4e57ccec9cece4824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631055"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>Visão geral do componente SaveFileDialog (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.SaveFileDialog> componente é uma caixa de diálogo pré-configurada. É o mesmo que o padrão **salvar arquivo** caixa de diálogo usada pelo Windows. Ele herda o <xref:System.Windows.Forms.CommonDialog> classe.  
  
## <a name="working-with-the-savefiledialog-component"></a>Trabalhando com o componente SaveFileDialog  
 Usá-lo como uma solução simples para habilitar os usuários salvem arquivos em vez de configurar sua própria caixa de diálogo. Confiando nas caixas de diálogo padrão do Windows, a funcionalidade básica de aplicativos que você criou é imediatamente familiar aos usuários. Lembre-se, no entanto, que, quando usar o <xref:System.Windows.Forms.SaveFileDialog> componente, você deve escrever sua própria lógica de salvamento do arquivo.  
  
 Você pode usar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução. Você pode abrir um arquivo no modo de leitura/gravação usando o <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> método.  
  
 Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.SaveFileDialog> componente aparece na bandeja na parte inferior do Designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.SaveFileDialog>
- [Componente SaveFileDialog](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)

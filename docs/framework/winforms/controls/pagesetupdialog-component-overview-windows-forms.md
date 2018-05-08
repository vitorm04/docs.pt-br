---
title: Visão geral do componente PageSetupDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 4e7b4548f5a178ed7b819dbc2edc37bb95e3e0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>Visão geral do componente PageSetupDialog (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PageSetupDialog> componente é uma caixa de diálogo pré-configurado usada para definir os detalhes de página de impressão em aplicativos baseados no Windows. Usá-lo em seu aplicativo do Windows como uma solução simples para os usuários para definir as preferências de página em vez de configurar sua própria caixa de diálogo. Você pode habilitar os usuários definam ajustes de borda e margem, cabeçalhos e rodapés de páginas e orientação retrato ou paisagem. Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários.  
  
## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla  
 Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução. Este componente tem propriedades que você pode definir relacionados como uma única página (<xref:System.Drawing.Printing.PrintDocument> classe) ou qualquer documento (<xref:System.Drawing.Printing.PageSettings> classe). Além disso, o <xref:System.Windows.Forms.PageSetupDialog> componente pode ser usado para determinar as configurações de impressora específica, que são armazenadas na <xref:System.Drawing.Printing.PrinterSettings> classe.  
  
 Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.PageSetupDialog> componente aparece na bandeja de na parte inferior do Designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [Componente PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)

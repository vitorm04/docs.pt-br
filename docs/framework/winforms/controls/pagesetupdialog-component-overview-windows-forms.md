---
title: Visão geral do componente PageSetupDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 989183b6152dfccb6167d89433317cea596d83c5
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211735"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>Visão geral do componente PageSetupDialog (Windows Forms)

Os formulários do Windows <xref:System.Windows.Forms.PageSetupDialog> componente é uma caixa de diálogo pré-configurada usada para definir os detalhes da página para impressão em aplicativos baseados no Windows. Use-o dentro de seu aplicativo com base em Windows, como uma solução simples para os usuários para definir preferências de página em vez de configurar sua própria caixa de diálogo. Você pode habilitar os usuários definam os ajustes de borda e margem, cabeçalhos e rodapés de páginas e orientação retrato ou paisagem. Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários.

## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla

Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução. Este componente tem propriedades que podem ser definidas e relacionadas a uma única página (<xref:System.Drawing.Printing.PrintDocument> classe) ou de quaisquer documentos (<xref:System.Drawing.Printing.PageSettings> classe). Além disso, o <xref:System.Windows.Forms.PageSetupDialog> componente pode ser usado para determinar as configurações de impressora específica, que são armazenadas em do <xref:System.Drawing.Printing.PrinterSettings> classe.

Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.PageSetupDialog> componente aparece na bandeja na parte inferior do Designer de formulários do Windows no Visual Studio.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PageSetupDialog>
- [Componente PageSetupDialog](pagesetupdialog-component-windows-forms.md)

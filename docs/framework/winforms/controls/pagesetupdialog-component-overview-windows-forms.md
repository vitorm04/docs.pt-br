---
title: Visão geral do componente PageSetupDialog
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744331"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>Visão geral do componente PageSetupDialog (Windows Forms)

O componente Windows Forms <xref:System.Windows.Forms.PageSetupDialog> é uma caixa de diálogo pré-configurada usada para definir detalhes da página para impressão em aplicativos baseados no Windows. Use-o em seu aplicativo baseado no Windows como uma solução simples para que os usuários definam preferências de página no lugar de configurar sua própria caixa de diálogo. Você pode permitir que os usuários definam ajustes de borda e margem, cabeçalhos e rodapés e orientação retrato ou paisagem. Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários.

## <a name="key-properties-and-methods"></a>Propriedades e métodos de tecla

Use o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo em tempo de execução. Esse componente tem propriedades que podem ser definidas com relação a uma única página (<xref:System.Drawing.Printing.PrintDocument> classe) ou a qualquer documento (<xref:System.Drawing.Printing.PageSettings> classe). Além disso, o componente <xref:System.Windows.Forms.PageSetupDialog> pode ser usado para determinar configurações de impressora específicas, que são armazenadas na classe <xref:System.Drawing.Printing.PrinterSettings>.

Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.PageSetupDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.PageSetupDialog>
- [Componente PageSetupDialog](pagesetupdialog-component-windows-forms.md)

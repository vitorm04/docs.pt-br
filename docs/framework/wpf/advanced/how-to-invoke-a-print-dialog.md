---
title: Como invocar uma caixa de diálogo Imprimir
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 6d7bc322079718d17a921ef34af79145b021e3a7
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636088"
---
# <a name="how-to-invoke-a-print-dialog"></a>Como invocar uma caixa de diálogo Imprimir
Para fornecer a capacidade de imprimir a partir do seu aplicativo, você pode simplesmente criar e abrir um objeto <xref:System.Windows.Controls.PrintDialog>.  
  
## <a name="example"></a>Exemplo  
 O controle de <xref:System.Windows.Controls.PrintDialog> fornece um único ponto de entrada para envio de trabalho de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuração e XPS. O controle é fácil de usar e pode ser instanciado usando marcação ou código [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. O exemplo a seguir demonstra como instanciar e abrir o controle no código e como imprimir por meio dele. Também mostra como assegurar que o diálogo dê ao usuário a opção de definir um intervalo específico de páginas. O código do exemplo pressupõe que existe um arquivo FixedDocumentSequence.xps na raiz da unidade C:.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Uma vez que a caixa de diálogo estiver aberta, os usuários poderão selecionar as impressoras instaladas em seu computador. Eles também terão a opção de selecionar o [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) para criar um arquivo XPS (XML Paper Specification) em vez de imprimir.  
  
> [!NOTE]
> O controle <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> do WPF, que é discutido neste tópico, não deve ser confundido com o componente <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> do Windows Forms.  
  
 Estritamente falando, você pode usar o método <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> sem nunca abrir a caixa de diálogo. Assim, o controle pode ser utilizado como um componente de impressão não visto. Mas, por motivos de desempenho, seria melhor usar o método <xref:System.Printing.PrintQueue.AddJob%2A> ou um dos muitos métodos <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> do <xref:System.Windows.Xps.XpsDocumentWriter>. Para saber mais, consulte [Impressão Programada de Arquivos XPS](how-to-programmatically-print-xps-files.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Controls.PrintDialog>
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
- [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)

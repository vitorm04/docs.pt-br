---
title: 'Como: Definir uma tabela com XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 011f612527f0c9e89ec05643edbb95b2d908488c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776566"
---
# <a name="how-to-define-a-table-with-xaml"></a>Como: Definir uma tabela com XAML
O exemplo a seguir demonstra como definir um <xref:System.Windows.Documents.Table> usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  A tabela de exemplo tem quatro colunas (representado por <xref:System.Windows.Documents.TableColumn> elementos) e várias linhas (representadas por <xref:System.Windows.Documents.TableRow> elementos) que contém os dados também, título, cabeçalho e rodapé informações.  Linhas devem estar contidas em um <xref:System.Windows.Documents.TableRowGroup> elemento.  Cada linha na tabela é composta de uma ou mais células (representado por <xref:System.Windows.Documents.TableCell> elementos).  Conteúdo em uma célula de tabela deve estar contido em um <xref:System.Windows.Documents.Block> elemento; nesse caso, <xref:System.Windows.Documents.Paragraph> elementos são usados.  A tabela também hospeda um hiperlink (representado pelo <xref:System.Windows.Documents.Hyperlink> elemento) na linha de rodapé.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 A figura a seguir mostra como a tabela definida neste exemplo é renderizado:  
  
 ![Captura de tela de uma tabela definida com XAML.](./media/how-to-define-a-table-with-xaml/planetary-information-xaml-table.png)

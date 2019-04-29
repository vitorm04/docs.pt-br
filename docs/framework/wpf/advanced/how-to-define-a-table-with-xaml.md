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
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="0bbf7-102">Como: Definir uma tabela com XAML</span><span class="sxs-lookup"><span data-stu-id="0bbf7-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="0bbf7-103">O exemplo a seguir demonstra como definir um <xref:System.Windows.Documents.Table> usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bbf7-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="0bbf7-104">A tabela de exemplo tem quatro colunas (representado por <xref:System.Windows.Documents.TableColumn> elementos) e várias linhas (representadas por <xref:System.Windows.Documents.TableRow> elementos) que contém os dados também, título, cabeçalho e rodapé informações.</span><span class="sxs-lookup"><span data-stu-id="0bbf7-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="0bbf7-105">Linhas devem estar contidas em um <xref:System.Windows.Documents.TableRowGroup> elemento.</span><span class="sxs-lookup"><span data-stu-id="0bbf7-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="0bbf7-106">Cada linha na tabela é composta de uma ou mais células (representado por <xref:System.Windows.Documents.TableCell> elementos).</span><span class="sxs-lookup"><span data-stu-id="0bbf7-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="0bbf7-107">Conteúdo em uma célula de tabela deve estar contido em um <xref:System.Windows.Documents.Block> elemento; nesse caso, <xref:System.Windows.Documents.Paragraph> elementos são usados.</span><span class="sxs-lookup"><span data-stu-id="0bbf7-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="0bbf7-108">A tabela também hospeda um hiperlink (representado pelo <xref:System.Windows.Documents.Hyperlink> elemento) na linha de rodapé.</span><span class="sxs-lookup"><span data-stu-id="0bbf7-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bbf7-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bbf7-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="0bbf7-110">A figura a seguir mostra como a tabela definida neste exemplo é renderizado:</span><span class="sxs-lookup"><span data-stu-id="0bbf7-110">The following figure shows how the table defined in this example renders:</span></span>  
  
 ![Captura de tela de uma tabela definida com XAML.](./media/how-to-define-a-table-with-xaml/planetary-information-xaml-table.png)

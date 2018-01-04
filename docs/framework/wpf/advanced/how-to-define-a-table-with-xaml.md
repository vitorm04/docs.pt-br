---
title: Como definir uma tabela com XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b932c7df822edabc5626f20af2bfc1eb3a7f93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="06815-102">Como definir uma tabela com XAML</span><span class="sxs-lookup"><span data-stu-id="06815-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="06815-103">O exemplo a seguir demonstra como definir um <xref:System.Windows.Documents.Table> usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06815-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="06815-104">A tabela de exemplo tem quatro colunas (representadas por <xref:System.Windows.Documents.TableColumn> elementos) e várias linhas (representado por <xref:System.Windows.Documents.TableRow> elementos) que contém dados, bem como título, cabeçalho e rodapé informações.</span><span class="sxs-lookup"><span data-stu-id="06815-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="06815-105">Linhas devem estar contidas em um <xref:System.Windows.Documents.TableRowGroup> elemento.</span><span class="sxs-lookup"><span data-stu-id="06815-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="06815-106">Cada linha na tabela é composta de uma ou mais células (representadas por <xref:System.Windows.Documents.TableCell> elementos).</span><span class="sxs-lookup"><span data-stu-id="06815-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="06815-107">Conteúdo em uma célula de tabela deve estar contido em um <xref:System.Windows.Documents.Block> elemento; nesse caso <xref:System.Windows.Documents.Paragraph> elementos são usados.</span><span class="sxs-lookup"><span data-stu-id="06815-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="06815-108">A tabela também hospeda um hiperlink (representado pelo <xref:System.Windows.Documents.Hyperlink> elemento) na linha de rodapé.</span><span class="sxs-lookup"><span data-stu-id="06815-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06815-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06815-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="06815-110">A figura a seguir mostra como a tabela definida neste exemplo é renderizado.</span><span class="sxs-lookup"><span data-stu-id="06815-110">The following figure shows how the table defined in this example renders.</span></span>  
  
 <span data-ttu-id="06815-111">![Tabela renderizada. ] (../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span><span class="sxs-lookup"><span data-stu-id="06815-111">![Rendered table.](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span></span>

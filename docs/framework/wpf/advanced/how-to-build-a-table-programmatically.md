---
title: "Como compilar uma tabela de forma programática"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fca6a304ea12dd90a71f8718fed5f1595f4cd4b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-table-programmatically"></a>Como compilar uma tabela de forma programática
Os exemplos a seguir mostram como criar programaticamente um <xref:System.Windows.Documents.Table> e preenchê-la com conteúdo. O conteúdo da tabela é particionado em cinco linhas (representadas por <xref:System.Windows.Documents.TableRow> objetos contidos em um <xref:System.Windows.Documents.Table.RowGroups%2A> objeto) e seis colunas (representado por <xref:System.Windows.Documents.TableColumn> objetos). As linhas são usadas para fins de apresentação diferentes, incluindo uma linha de título para ser usada como título da tabela inteira, uma linha de cabeçalho para descrever as colunas de dados na tabela e uma linha de rodapé com informações resumidas.  Observe que a noção das linhas de “título”, “cabeçalho” e “rodapé” não são inerentes à tabela; essas são apenas linhas com características diferentes. Células de tabela contêm o conteúdo real, que pode ser composto de texto, imagens ou quase qualquer outro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elemento.  
  
## <a name="example"></a>Exemplo  
 Primeiro, um <xref:System.Windows.Documents.FlowDocument> é criado para hospedar o <xref:System.Windows.Documents.Table>e um novo <xref:System.Windows.Documents.Table> é criado e adicionado ao conteúdo do <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a>Exemplo  
 Em seguida, seis <xref:System.Windows.Documents.TableColumn> objetos são criados e adicionados à tabela de <xref:System.Windows.Documents.Table.Columns%2A> coleção, com alguma formatação aplicada.  
  
> [!NOTE]
>  Observe que a tabela <xref:System.Windows.Documents.Table.Columns%2A> coleção usa a indexação com base em zero padrão.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a>Exemplo  
 Em seguida, uma linha de título é criada e adicionada à tabela com certa formatação aplicada.  Por coincidência, a linha de título contém uma única célula que abrange todas as seis colunas na tabela.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a>Exemplo  
 Em seguida, uma linha de cabeçalho é criada e adicionada à tabela e as células na linha de cabeçalho são criadas e populadas com conteúdo.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a>Exemplo  
 Em seguida, uma linha para os dados é criada e adicionada à tabela, e as células nesta linha são criadas e populadas com conteúdo.  A criação dessa linha é semelhante à criação da linha de cabeçalho, com uma formatação ligeiramente diferente aplicada.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a>Exemplo  
 Por fim, uma linha de rodapé é criada, adicionada e formatada.  Como a linha de título, o rodapé contém uma única célula que abrange todas as seis colunas na tabela.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da tabela](../../../../docs/framework/wpf/advanced/table-overview.md)

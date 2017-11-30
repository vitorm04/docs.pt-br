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
ms.openlocfilehash: 350dff0b6ea9d92e919e45e4f46cf888f44f6212
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-define-a-table-with-xaml"></a>Como definir uma tabela com XAML
O exemplo a seguir demonstra como definir um <xref:System.Windows.Documents.Table> usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  A tabela de exemplo tem quatro colunas (representadas por <xref:System.Windows.Documents.TableColumn> elementos) e várias linhas (representado por <xref:System.Windows.Documents.TableRow> elementos) que contém dados, bem como título, cabeçalho e rodapé informações.  Linhas devem estar contidas em um <xref:System.Windows.Documents.TableRowGroup> elemento.  Cada linha na tabela é composta de uma ou mais células (representadas por <xref:System.Windows.Documents.TableCell> elementos).  Conteúdo em uma célula de tabela deve estar contido em um <xref:System.Windows.Documents.Block> elemento; nesse caso <xref:System.Windows.Documents.Paragraph> elementos são usados.  A tabela também hospeda um hiperlink (representado pelo <xref:System.Windows.Documents.Hyperlink> elemento) na linha de rodapé.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 A figura a seguir mostra como a tabela definida neste exemplo é renderizado.  
  
 ![Tabela renderizada. ] (../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")

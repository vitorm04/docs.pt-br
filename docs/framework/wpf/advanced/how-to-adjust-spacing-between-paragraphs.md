---
title: 'Como: Ajustar o espaçamento entre parágrafos'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367473"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>Como: Ajustar o espaçamento entre parágrafos
Este exemplo mostra como ajustar ou eliminar o espaçamento entre parágrafos em conteúdo de fluxo.  
  
 No conteúdo de fluxo, o espaço extra que aparece entre parágrafos é o resultado de margens definidas destes parágrafos; Portanto, o espaçamento entre parágrafos pode ser controlado ajustando as margens daqueles parágrafos.  Para eliminar completamente o espaço extra entre dois parágrafos, defina as margens dos parágrafos para **0**.  Para obter o espacejamento uniforme entre parágrafos em todo <xref:System.Windows.Documents.FlowDocument>, use estilos para definir um valor de margem uniforme para todos os parágrafos no <xref:System.Windows.Documents.FlowDocument>.  
  
 É importante observar que as margens de dois parágrafos adjacentes "se recolherão" para a maior das margens, em vez de dobrar. Portanto, se dois parágrafos adjacentes possuírem margens de 20 pixels e 40 pixels respectivamente, o espaço entre os parágrafos resultante será de 40 pixels, o maior dos dois valores de margem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir utiliza estilos para configurar a margem para todos os <xref:System.Windows.Documents.Paragraph> elementos em um <xref:System.Windows.Documents.FlowDocument> à **0**, que elimina efetivamente o espaço extra entre parágrafos no <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]

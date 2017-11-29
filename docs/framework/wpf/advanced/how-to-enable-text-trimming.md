---
title: Como habilitar filtragem de texto
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
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8f0f24bb6271e63dc50bd063aedfd8185711e7a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-text-trimming"></a>Como habilitar filtragem de texto
Este exemplo demonstra o uso e efeitos dos valores disponíveis no <xref:System.Windows.TextTrimming> enumeração.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma <xref:System.Windows.Controls.TextBlock> elemento com o <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> conjunto de atributos.  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a>Exemplo  
 Definindo a correspondente <xref:System.Windows.TextTrimming> propriedade no código é demonstrada abaixo.  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 Existem atualmente três opções para quebra de texto: **CharacterEllipsis**, **WordEllipsis**, e **nenhum**.  
  
 Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **CharacterEllipsis**, o texto é cortado e continuado com uma elipse no caractere mais próximo à quina de corte.  Essa configuração tende a cortar o texto para se ajustar mais bem ao limite de corte, mas pode resultar em palavras parcialmente cortadas.  A figura a seguir mostra o efeito dessa configuração em uma <xref:System.Windows.Controls.TextBlock> semelhante àquela definida acima.  
  
 ![Example: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")  
  
 Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **WordEllipsis**, o texto é cortado e continuado com uma elipse ao final da primeira palavra mais próxima à quina de corte.  Essa configuração não mostra palavras parcialmente quebradas, mas tende a não quebrar o texto mais próximo à quina de corte quanto o **CharacterEllipsis** configuração.  A figura a seguir mostra o efeito dessa configuração no <xref:System.Windows.Controls.TextBlock> definida acima.  
  
 ![Exemplo: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")  
  
 Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **nenhum**, nenhuma quebra de texto é realizada.  Nesse caso, o texto é simplesmente recortado para o limite do contêiner de texto pai.  A figura a seguir mostra o efeito dessa configuração em uma <xref:System.Windows.Controls.TextBlock> semelhante àquela definida acima.  
  
 ![Exemplo: TextTrimming. None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")

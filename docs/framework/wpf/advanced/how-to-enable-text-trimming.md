---
title: Como habilitar filtragem de texto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 97bc88b298500892fcc7d26e61f8052a05d9e593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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

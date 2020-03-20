---
title: Como criar texto com uma sombra
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186843"
---
# <a name="how-to-create-text-with-a-shadow"></a>Como criar texto com uma sombra
Os exemplos nesta seção mostram como criar um efeito de sombra para texto exibido.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.Effects.DropShadowEffect> objeto permite criar uma variedade de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] efeitos de sombra projetada para objetos. O exemplo a seguir mostra um efeito de sombra aplicado ao texto. Nesse caso, a sombra é suave, o que significa que a cor da sombra é desfocada.  
  
 ![Sombra de texto com Maciez &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 Você pode controlar a largura de <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> uma sombra definindo a propriedade. Um valor `4.0` de indica uma largura de sombra de 4 pixels. Você pode controlar a maciez, ou borrar, de uma sombra modificando a <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade. Um valor `0.0` de não indica embaçamento. O exemplo de código a seguir mostra como criar uma sombra suave.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Esses efeitos de sombra [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] não passam pelo pipeline de renderização de texto. Como resultado, ClearType fica desabilitado ao usar esses efeitos.  
  
 O exemplo a seguir mostra um efeito de sombra sólida aplicado ao texto. Nesse caso, a sombra não está desfocada.  
  
 ![Sombra de texto com Maciez &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 Você pode criar uma sombra <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> dura `0.0`definindo a propriedade para , o que indica que nenhum borrão é usado. Você pode controlar a direção da <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> sombra modificando a propriedade. Defina o valor direcional desta `0` propriedade `360`em um grau entre e . A ilustração a seguir mostra <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> os valores direcionais da configuração da propriedade.  
  
 ![Configuração de grau de sombra de DropShadow](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 O exemplo de código a seguir mostra como criar uma sombra sólida.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Usando um efeito de desfoque  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> pode ser usado para criar um efeito semelhante à sombra que pode ser colocado atrás de um objeto de texto. Um efeito de bitmap de desfoque aplicado ao texto desfoca o texto uniformemente em todas as direções.  
  
 O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.  
  
 ![Sombra de texto usando BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 O exemplo de código a seguir mostra como criar um efeito de desfoque.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Usando uma transformação de movimentação  
 A <xref:System.Windows.Media.TranslateTransform> pode ser usado para criar um efeito semelhante à sombra que pode ser colocado atrás de um objeto de texto.  
  
 O exemplo de <xref:System.Windows.Media.TranslateTransform> código a seguir usa um texto para compensar. Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.  
  
 ![Sombra de texto usando TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 O exemplo de código a seguir mostra como criar uma transformação para um efeito de sombra.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]

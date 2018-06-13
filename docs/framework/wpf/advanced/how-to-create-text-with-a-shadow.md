---
title: Como criar texto com uma sombra
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 1b7740284afcda6eab41fb68be3b4a2f032cc77d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544752"
---
# <a name="how-to-create-text-with-a-shadow"></a>Como criar texto com uma sombra
Os exemplos nesta seção mostram como criar um efeito de sombra para texto exibido.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.Effects.DropShadowEffect> objeto permite que você crie uma variedade de efeitos de sombra para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objetos. O exemplo a seguir mostra um efeito de sombra aplicado ao texto. Nesse caso, a sombra é suave, o que significa que a cor da sombra é desfocada.  
  
 ![Sombra de texto com Suavidade &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Exemplo de texto com uma sombra suave  
  
 Você pode controlar a largura de uma sombra definindo a <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> propriedade. Um valor de `4.0` indica uma sombra de 4 pixels de largura. Você pode controlar a suavidade de uma sombra modificando o <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade. Um valor de `0.0` não indica nenhum obscurecendo. O exemplo de código a seguir mostra como criar uma sombra suave.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Esses efeitos de sombra não vão para o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pipeline de processamento de texto. Como resultado, ClearType fica desabilitado ao usar esses efeitos.  
  
 O exemplo a seguir mostra um efeito de sombra sólida aplicado ao texto. Nesse caso, a sombra não está desfocada.  
  
 ![Sombra de texto com Suavidade &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")  
Exemplo de texto com uma sombra sólida  
  
 Você pode criar uma sombra sólida definindo a <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade `0.0`, indicando que nenhum obscurecendo é usada. Você pode controlar a direção da sombra modificando o <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> propriedade. Defina o valor direcional desta propriedade como um grau entre `0` e `360`. A ilustração a seguir mostra os valores direcionais do <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> configuração de propriedade.  
  
 ![Configuração de grau de sombra da sombra](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
Diagrama de direção de DropShadow  
  
 O exemplo de código a seguir mostra como criar uma sombra sólida.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Usando um efeito de desfoque  
 Um <xref:System.Windows.Media.Effects.BlurBitmapEffect> pode ser usado para criar um efeito semelhante a sombra que pode ser colocado por trás de um objeto de texto. Um efeito de bitmap de desfoque aplicado ao texto desfoca o texto uniformemente em todas as direções.  
  
 O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.  
  
 ![Sombra de texto usando BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Exemplo de texto com um efeito de desfoque  
  
 O exemplo de código a seguir mostra como criar um efeito de desfoque.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Usando uma transformação de movimentação  
 Um <xref:System.Windows.Media.TranslateTransform> pode ser usado para criar um efeito semelhante a sombra que pode ser colocado por trás de um objeto de texto.  
  
 O seguinte exemplo de código usa um <xref:System.Windows.Media.TranslateTransform> para deslocar texto. Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.  
  
 ![Sombra de texto usando TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")  
Exemplo de texto usando uma transformação para efeito de sombra  
  
 O exemplo de código a seguir mostra como criar uma transformação para um efeito de sombra.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]

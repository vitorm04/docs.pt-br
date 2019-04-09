---
title: 'Como: Usar chaves de parâmetros do sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 147f65b4bb214c12317309081c345251d7426cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147323"
---
# <a name="how-to-use-system-parameters-keys"></a>Como: Usar chaves de parâmetros do sistema
Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemParameters> é uma classe que contém os valores de parâmetro do sistema e as chaves associadas aos valores — por exemplo, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> e <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Métricas de parâmetro do sistema podem ser usadas como recursos estáticos ou dinâmicos. Use um recurso dinâmico se desejar que a métrica de parâmetro atualize automaticamente enquanto o aplicativo é executado; Caso contrário, use um recurso estático.  
  
> [!NOTE]
>  Recursos dinâmicos têm a palavra-chave *chave* acrescentado ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar recursos dinâmicos de parâmetros de sistema para estilizar ou personalizar um botão. Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo dimensiona um botão atribuindo <xref:System.Windows.SystemParameters> valores para a largura e a altura do botão.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Consulte também

- [Pintar uma área com um pincel de sistema](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Usar SystemFonts](how-to-use-systemfonts.md)
- [Usar SystemParameters](how-to-use-systemparameters.md)

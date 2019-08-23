---
title: 'Como: Usar chaves de fontes do sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918380"
---
# <a name="how-to-use-system-fonts-keys"></a>Como: Usar chaves de fontes do sistema
Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemFonts>é uma classe que contém valores de fontes do sistema e recursos de fontes do sistema que se associam aos valores <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> — <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>por exemplo, e.  
  
 As métricas de fonte do sistema podem ser usadas como recursos estáticos ou dinâmicos. Use um recurso dinâmico se desejar que a métrica da fonte seja atualizada automaticamente enquanto o aplicativo é executado; caso contrário, use um recurso estático.  
  
> [!NOTE]
> Os recursos dinâmicos têm a *tecla* keyword anexada ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar recursos dinâmicos de fonte do sistema para estilizar ou personalizar um botão. Este [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo cria um estilo de botão que <xref:System.Windows.SystemFonts> atribui valores a um botão.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Consulte também

- [Pintar uma área com um pincel de sistema](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Usar SystemParameters](how-to-use-systemparameters.md)
- [Usar SystemFonts](how-to-use-systemfonts.md)

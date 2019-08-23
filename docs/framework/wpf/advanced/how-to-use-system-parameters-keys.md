---
title: 'Como: Usar chaves de parâmetros do sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918379"
---
# <a name="how-to-use-system-parameters-keys"></a>Como: Usar chaves de parâmetros do sistema
Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemParameters>é uma classe que contém os valores de parâmetro do sistema e as chaves de recurso que se associam aos <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> valores <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>— por exemplo, e. As métricas de parâmetro do sistema podem ser usadas como recursos estáticos ou dinâmicos. Use um recurso dinâmico se desejar que a métrica de parâmetro seja atualizada automaticamente enquanto o aplicativo for executado; caso contrário, use um recurso estático.  
  
> [!NOTE]
> Os recursos dinâmicos têm a *tecla* keyword anexada ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar recursos dinâmicos de parâmetros do sistema para estilizar ou personalizar um botão. Este [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo dimensiona um botão <xref:System.Windows.SystemParameters> atribuindo valores à largura e à altura do botão.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Consulte também

- [Pintar uma área com um pincel de sistema](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Usar SystemFonts](how-to-use-systemfonts.md)
- [Usar SystemParameters](how-to-use-systemparameters.md)

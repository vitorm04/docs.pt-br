---
title: 'Como: Usar layout automático para criar um botão'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 185bf71d4105d10a2bb85e6a0abd9da63c7d26f0
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185448"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Como: Usar layout automático para criar um botão
Este exemplo descreve como usar a abordagem de layout automático para criar um botão em um aplicativo localizável.  
  
 Localização de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pode ser um processo demorado. Geralmente, localizadores precisam redimensionar e reposicionar elementos além de traduzir o texto. No passado cada idioma que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado exigia um ajuste. Agora, com os recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] você pode criar elementos que reduzem a necessidade de ajuste. A abordagem para escrever aplicativos que podem ser mais facilmente redimensionados e reposicionados é chamada `automatic layout`.  
  
## <a name="example"></a>Exemplo  

Os dois seguintes [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos criam aplicativos que criar uma instância de um botão, uma com texto em inglês e outra com texto em espanhol. Observe que o código é o mesmo, exceto para o texto; o botão é ajustada para se ajustar ao texto.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 O gráfico a seguir mostra a saída dos exemplos de código.  
  
 ![O mesmo botão com texto em diferentes idiomas](./media/globalizationbutton.png "GlobalizationButton")  
Botão redimensionável automaticamente  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do uso de layout automático](use-automatic-layout-overview.md)
- [Usar uma grade para layout automático](how-to-use-a-grid-for-automatic-layout.md)

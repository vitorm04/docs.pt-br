---
title: "Como usar uma grade para layout automático"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbd8bd7e36b7b773837b839e77ec88a8e7c8f0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>Como usar uma grade para layout automático
Este exemplo descreve como usar uma grade na abordagem de layout automático para criar um aplicativo localizável.  
  
 Localização de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] pode ser um processo demorado. Geralmente, localizadores precisam redimensionar e reposicionar elementos além de traduzir o texto. No passado cada idioma que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] foi adaptado para ajuste necessário. Agora com os recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] você pode criar elementos que reduzem a necessidade de ajuste. A abordagem para escrever aplicativos que podem ser reposicionado e redimensionado mais facilmente é chamada `auto layout`.  
  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo demonstra o uso de uma grade para posicionar alguns botões e texto. Observe que a altura e largura das células são definidas como `Auto`; portanto, a célula que contém o botão com uma imagem ajusta para ajustar a imagem. Porque o <xref:System.Windows.Controls.Grid> elemento pode ajustar a seu conteúdo pode ser útil quando seguirmos a abordagem de layout automático para projetar aplicativos que podem ser localizados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar uma grade.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 O gráfico a seguir mostra a saída do exemplo de código.  
  
 ![Exemplo de grade](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Grade  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do uso de layout automático](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Usar layout automático para criar um botão](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)

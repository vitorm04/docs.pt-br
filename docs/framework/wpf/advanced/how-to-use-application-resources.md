---
title: 'Como: Usar recursos do aplicativo'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 70dff8089c4da70fdc61247a0c604cf7ee85d02b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088191"
---
# <a name="how-to-use-application-resources"></a>Como: Usar recursos do aplicativo
Esse exemplo demonstra como usar recursos do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um arquivo de definição de aplicativo. O arquivo de definição de aplicativo define uma seção de recursos (um valor para o <xref:System.Windows.Application.Resources%2A> propriedade). Recursos definidos no nível do aplicativo podem ser acessados por todas as outras páginas que fazem parte do aplicativo. Nesse caso, o recurso é um estilo declarado. Como um estilo completo que inclui um modelo de controle pode ser demorado, este exemplo omite o modelo de controle que é definido dentro de <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> setter de propriedade do estilo.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 A exemplo a seguir mostra um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] página que faz referência ao recurso de nível de aplicativo que o exemplo anterior definiu. O recurso referenciado usando um [extensão de marcação StaticResource](staticresource-markup-extension.md) que especifica a chave de recurso exclusivo para o recurso solicitado. Nenhum recurso com chave de "GelButton" é encontrado na página atual, portanto, o escopo da pesquisa de recursos para o recurso solicitado continua além da página atual e até os recursos de nível de aplicativo definidos.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Consulte também

- [Recursos XAML](xaml-resources.md)
- [Visão geral de gerenciamento do aplicativo](../app-development/application-management-overview.md)
- [Tópicos explicativos ](resources-how-to-topics.md)

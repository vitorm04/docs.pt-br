---
title: Como usar recursos do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460260"
---
# <a name="how-to-use-application-resources"></a>Como usar recursos do aplicativo
Esse exemplo demonstra como usar recursos do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um arquivo de definição de aplicativo. O arquivo de definição de aplicativo define uma seção de recurso (um valor para a propriedade <xref:System.Windows.Application.Resources%2A>). Recursos definidos no nível do aplicativo podem ser acessados por todas as outras páginas que fazem parte do aplicativo. Nesse caso, o recurso é um estilo declarado. Como um estilo completo que inclui um modelo de controle pode ser longo, este exemplo omite o modelo de controle que é definido no setter da propriedade de <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> do estilo.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 O exemplo a seguir mostra uma página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que faz referência ao recurso de nível de aplicativo que o exemplo anterior definiu. O recurso é referenciado usando uma [extensão de marcação StaticResource](staticresource-markup-extension.md) que especifica a chave de recurso exclusiva para o recurso solicitado. Nenhum recurso com chave de "GelButton" é encontrado na página atual, portanto, o escopo da pesquisa de recursos para o recurso solicitado continua além da página atual e até os recursos de nível de aplicativo definidos.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Consulte também

- [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Visão geral do gerenciamento de aplicativos](../app-development/application-management-overview.md)
- [Tópicos explicativos](resources-how-to-topics.md)

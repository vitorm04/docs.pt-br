---
title: "Como associar a um serviço Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b035f5922722a05759ff1e13514cc760a57d668
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-web-service"></a>Como associar a um serviço Web
Este exemplo mostra como associar a objetos retornados por chamadas de método de serviço Web.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o [serviço de conteúdo de sistema de publicação MSDN/TechNet (MTPS)](http://go.microsoft.com/fwlink/?LinkId=95677) para recuperar a lista de idiomas com suporte de um documento especificado.  
  
 Antes de chamar um serviço Web, é necessário criar uma referência a ele. Para criar uma referência Web ao serviço MTPS usando [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], siga as etapas a seguir:  
  
1.  Abra o projeto no [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  
  
2.  No menu **Projeto**, clique em **Adicionar referência Web**.  
  
3.  Na caixa de diálogo, defina o **URL** como [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4.  Pressione **Ir** e, em seguida, **Adicionar referência**.  
  
 Em seguida, chame o método de serviço Web e defina o <xref:System.Windows.FrameworkElement.DataContext%2A> do controle apropriado ou da janela para o objeto retornado. O método **GetContent** do serviço MTPS utiliza uma referência para o objeto **getContentRequest**. Portanto, o exemplo a seguir primeiro define um objeto de solicitação:  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Após o <xref:System.Windows.FrameworkElement.DataContext%2A> tiver sido definido, você pode criar associações com as propriedades do objeto que o <xref:System.Windows.FrameworkElement.DataContext%2A> foi definido como. Neste exemplo, o <xref:System.Windows.FrameworkElement.DataContext%2A> é definido como o **getContentResponse** objeto retornado pelo **GetContent** método. No exemplo a seguir, o <xref:System.Windows.Controls.ItemsControl> associa e exibe o **localidade** valores de **availableVersionsAndLocales** de **getContentResponse**.  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Para obter informações sobre a estrutura de **getContentResponse**, consulte a [Documentação do serviço de conteúdo](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Visão geral das origens da associação](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Disponibilizar dados para associação em XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)

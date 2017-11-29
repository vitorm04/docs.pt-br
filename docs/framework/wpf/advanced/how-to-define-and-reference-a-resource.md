---
title: Como definir e referenciar um recurso
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 322ac3e5ebfe2d820a4711d877396b9a1a2759a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-and-reference-a-resource"></a>Como definir e referenciar um recurso
Esse exemplo mostra como definir um recurso e fazer referência a ele usando um atributo em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define dois tipos de recursos: um <xref:System.Windows.Media.SolidColorBrush> recursos e várias <xref:System.Windows.Style> recursos. O <xref:System.Windows.Media.SolidColorBrush> recurso `MyBrush` é usada para fornecer o valor de várias propriedades que recebem um <xref:System.Windows.Media.Brush> tipo de valor. O <xref:System.Windows.Style> recursos `PageBackground`, `TitleText` e `Label` cada destino de um determinado tipo de controle. Os estilos definem uma variedade de diferentes propriedades nos controles de destino, quando o recurso de estilo é referenciado por chave de recurso e é usado para definir o <xref:System.Windows.FrameworkElement.Style%2A> propriedade de vários elementos de controle específicos definidos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Observe que uma das propriedades dentro dos setters do estilo `Label` também fazem referência ao recurso `MyBrush` definido anteriormente. Essa é uma técnica comum, mas é importante lembrar que os recursos são analisados e inseridos em um dicionário de recursos na ordem em que são apresentados. Recursos também serão solicitados pela ordem encontrada no dicionário se você usar a [Extensão de marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) para fazer referência a eles de dentro de outro recurso. Verifique se os recursos aos quais você fez referência são definidos anteriormente na coleção de recursos da qual esse recurso é solicitado. Se necessário, você pode contornar a ordem estrita de criação de referências de recursos usando uma [Extensão de marcação DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) para fazer referência ao recurso no tempo de execução, porém você sempre deve estar ciente que essa técnica DynamicResource traz consequências para o desempenho. Para ver mais detalhes, consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>Consulte também  
 [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)

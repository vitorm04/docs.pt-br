---
title: 'Como: Definir e referenciar um recurso'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 39cde252ce98e55f155edfb7a4c2268219d6858e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692867"
---
# <a name="how-to-define-and-reference-a-resource"></a>Como: Definir e referenciar um recurso
Esse exemplo mostra como definir um recurso e fazer referência a ele usando um atributo em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define dois tipos de recursos: um <xref:System.Windows.Media.SolidColorBrush> recursos e vários <xref:System.Windows.Style> recursos. O <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` é usado para fornecer o valor de várias propriedades que usam um <xref:System.Windows.Media.Brush> tipo de valor. O <xref:System.Windows.Style> recursos `PageBackground`, `TitleText` e `Label` cada um determinado tipo de controle de destino. Os estilos definem uma variedade de diferentes propriedades nos controles de destino, quando o recurso de estilo é referenciado por chave de recurso e é usado para definir a <xref:System.Windows.FrameworkElement.Style%2A> propriedade de vários elementos de controle específicos definidos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Observe que uma das propriedades dentro dos setters do estilo `Label` também fazem referência ao recurso `MyBrush` definido anteriormente. Essa é uma técnica comum, mas é importante lembrar que os recursos são analisados e inseridos em um dicionário de recursos na ordem em que são apresentados. Recursos também serão solicitados pela ordem encontrada no dicionário se você usar a [Extensão de marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) para fazer referência a eles de dentro de outro recurso. Verifique se os recursos aos quais você fez referência são definidos anteriormente na coleção de recursos da qual esse recurso é solicitado. Se necessário, você pode contornar a ordem estrita de criação de referências de recursos usando uma [Extensão de marcação DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) para fazer referência ao recurso no tempo de execução, porém você sempre deve estar ciente que essa técnica DynamicResource traz consequências para o desempenho. Para ver mais detalhes, consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>Consulte também
- [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)

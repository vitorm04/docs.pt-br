---
title: Como definir e referenciar um recurso
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: e33c86b03d8b18113f3a15b3ab251753958ff5b2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646504"
---
# <a name="how-to-define-and-reference-a-resource"></a>Como definir e referenciar um recurso

Esse exemplo mostra como definir um recurso e fazer referência a ele usando um atributo em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Exemplo

O exemplo a seguir define dois <xref:System.Windows.Media.SolidColorBrush> tipos de <xref:System.Windows.Style> recursos: um recurso e vários recursos. O <xref:System.Windows.Media.SolidColorBrush> `MyBrush` recurso é usado para fornecer o valor <xref:System.Windows.Media.Brush> de várias propriedades que cada uma leva um valor de tipo. Os <xref:System.Windows.Style> `PageBackground`recursos `TitleText` `Label` e cada um tem como alvo um tipo de controle específico. Os estilos definem uma variedade de propriedades diferentes nos controles direcionados, quando esse recurso <xref:System.Windows.FrameworkElement.Style%2A> de estilo é referenciado por chave de recurso e é usado para definir a propriedade de vários elementos de controle específicos definidos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

Observe que uma das propriedades dentro dos setters do estilo `Label` também fazem referência ao recurso `MyBrush` definido anteriormente. Essa é uma técnica comum, mas é importante lembrar que os recursos são analisados e inseridos em um dicionário de recursos na ordem em que são apresentados. Recursos também serão solicitados pela ordem encontrada no dicionário se você usar a [Extensão de marcação StaticResource](staticresource-markup-extension.md) para fazer referência a eles de dentro de outro recurso. Verifique se os recursos aos quais você fez referência são definidos anteriormente na coleção de recursos da qual esse recurso é solicitado. Se necessário, você pode contornar a ordem de criação estrita de referências de recursos usando uma [extensão de marcação de recursos dinâmicos](dynamicresource-markup-extension.md) para referenciar o recurso em tempo de execução, mas você deve estar ciente de que essa técnica DynamicResource tem consequências de desempenho. Para ver mais detalhes, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Confira também

- [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)

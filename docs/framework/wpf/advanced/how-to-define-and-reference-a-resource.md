---
title: Como definir e referenciar um recurso
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 89471c45aabd9f3415c45a2e8af41d1a52900324
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460180"
---
# <a name="how-to-define-and-reference-a-resource"></a>Como definir e referenciar um recurso

Esse exemplo mostra como definir um recurso e fazer referência a ele usando um atributo em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

## <a name="example"></a>Exemplo

O exemplo a seguir define dois tipos de recursos: um <xref:System.Windows.Media.SolidColorBrush> recurso e vários recursos de <xref:System.Windows.Style>. O `MyBrush` de recursos <xref:System.Windows.Media.SolidColorBrush> é usado para fornecer o valor de várias propriedades que cada um pega um valor de tipo de <xref:System.Windows.Media.Brush>. Os recursos de <xref:System.Windows.Style> `PageBackground`, `TitleText` e `Label` cada um visando um determinado tipo de controle. Os estilos definem uma variedade de propriedades diferentes nos controles de destino, quando esse recurso de estilo é referenciado pela chave de recurso e é usado para definir a propriedade <xref:System.Windows.FrameworkElement.Style%2A> de vários elementos de controle específicos definidos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

Observe que uma das propriedades dentro dos setters do estilo `Label` também fazem referência ao recurso `MyBrush` definido anteriormente. Essa é uma técnica comum, mas é importante lembrar que os recursos são analisados e inseridos em um dicionário de recursos na ordem em que são apresentados. Recursos também serão solicitados pela ordem encontrada no dicionário se você usar a [Extensão de marcação StaticResource](staticresource-markup-extension.md) para fazer referência a eles de dentro de outro recurso. Verifique se os recursos aos quais você fez referência são definidos anteriormente na coleção de recursos da qual esse recurso é solicitado. Se necessário, você pode contornar a ordem de criação estrita de referências de recursos usando uma [extensão de marcação DynamicResource](dynamicresource-markup-extension.md) para referenciar o recurso em tempo de execução, mas você deve estar ciente de que essa técnica DynamicResource tem desempenho consequências. Para ver mais detalhes, consulte [Recursos XAML](xaml-resources.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Consulte também

- [Recursos XAML](xaml-resources.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)

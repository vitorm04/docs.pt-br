---
title: Como implementar uma propriedade de dependência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: b0c5b33d841f43249f9559bd31f1ef8fe66ff05e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544642"
---
# <a name="how-to-implement-a-dependency-property"></a>Como implementar uma propriedade de dependência
Este exemplo mostra como fazer uma [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] propriedade com um <xref:System.Windows.DependencyProperty> campo, portanto, definir uma propriedade de dependência. Ao definir suas próprias propriedades, se deseja dar suporte a muitos aspectos de funcionalidades do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], incluindo estilos, vinculação de dados, herança, animação e valores padrão, você deve implementá-las como uma propriedade de dependência.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra pela primeira vez uma propriedade de dependência chamando o <xref:System.Windows.DependencyProperty.Register%2A> método. O nome do campo de identificador que você usa para armazenar o nome e características da propriedade de dependência devem ser o <xref:System.Windows.DependencyProperty.Name%2A> escolhido para a propriedade de dependência como parte do <xref:System.Windows.DependencyProperty.Register%2A> chamada anexada pela cadeia de caracteres literal `Property`. Por exemplo, se você registrar uma propriedade de dependência com um <xref:System.Windows.DependencyProperty.Name%2A> de `Location`, em seguida, o campo de identificador que você definir para a propriedade de dependência deve ser nomeado `LocationProperty`.  
  
 Neste exemplo, o nome da propriedade de dependência e sua [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] acessador é `State`; o campo identificador é `StateProperty`; o tipo da propriedade é <xref:System.Boolean>; e o tipo que registra a propriedade de dependência é `MyStateControl`.  
  
 Se você não conseguir seguir esse padrão de nomenclatura, os designers poderão não relatar sua propriedade corretamente e determinados aspectos do aplicativo de estilo do sistema de propriedade poderão não se comportar conforme o esperado.  
  
 Também é possível especificar metadados padrão para uma propriedade de dependência. Esse exemplo registra o valor padrão da propriedade de dependência `State` como `false`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Para obter mais informações sobre como e por que implementar uma propriedade de dependência, em vez de simplesmente dar suporte a uma propriedade [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com um campo privado, consulte a [Visão geral das propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)

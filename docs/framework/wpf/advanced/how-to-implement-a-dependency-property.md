---
title: 'Como: Implementar uma propriedade de dependência'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: e2f18cb3941be2ebf4315a844c05b91ff49c6aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757450"
---
# <a name="how-to-implement-a-dependency-property"></a>Como: Implementar uma propriedade de dependência
Este exemplo mostra como fazer uma [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] propriedade com um <xref:System.Windows.DependencyProperty> campo, assim, definindo uma propriedade de dependência. Ao definir suas próprias propriedades, se deseja dar suporte a muitos aspectos de funcionalidades do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], incluindo estilos, vinculação de dados, herança, animação e valores padrão, você deve implementá-las como uma propriedade de dependência.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra uma propriedade de dependência pela primeira vez chamando o <xref:System.Windows.DependencyProperty.Register%2A> método. O nome do campo de identificador que você usa para armazenar o nome e as características da propriedade de dependência devem ser o <xref:System.Windows.DependencyProperty.Name%2A> escolhida para a propriedade de dependência como parte do <xref:System.Windows.DependencyProperty.Register%2A> chamada, anexada pela cadeia de caracteres literal `Property`. Por exemplo, se você registrar uma propriedade de dependência com um <xref:System.Windows.DependencyProperty.Name%2A> dos `Location`, em seguida, o campo de identificador que você definir para a propriedade de dependência deve ser nomeado `LocationProperty`.  
  
 Neste exemplo, o nome da propriedade de dependência e seu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] acessador `State`; o campo identificador é `StateProperty`; o tipo da propriedade é <xref:System.Boolean>; e o tipo que registra a propriedade de dependência é `MyStateControl`.  
  
 Se você não conseguir seguir esse padrão de nomenclatura, os designers poderão não relatar sua propriedade corretamente e determinados aspectos do aplicativo de estilo do sistema de propriedade poderão não se comportar conforme o esperado.  
  
 Também é possível especificar metadados padrão para uma propriedade de dependência. Esse exemplo registra o valor padrão da propriedade de dependência `State` como `false`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Para obter mais informações sobre como e por que implementar uma propriedade de dependência, em vez de simplesmente dar suporte a uma propriedade [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com um campo privado, consulte a [Visão geral das propriedades de dependência](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Tópicos de instruções](properties-how-to-topics.md)

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
ms.openlocfilehash: 6f2fb9b0824feb6253527de063f58da2427d0c06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400360"
---
# <a name="how-to-implement-a-dependency-property"></a>Como: Implementar uma propriedade de dependência
Este exemplo mostra como fazer uma propriedade de Common Language Runtime (CLR) com um <xref:System.Windows.DependencyProperty> campo, definindo, portanto, uma propriedade de dependência. Ao definir suas próprias propriedades, se deseja dar suporte a muitos aspectos de funcionalidades do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], incluindo estilos, vinculação de dados, herança, animação e valores padrão, você deve implementá-las como uma propriedade de dependência.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra primeiro uma propriedade de dependência chamando <xref:System.Windows.DependencyProperty.Register%2A> o método. O nome do campo de identificador que você usa para armazenar o nome e as características da propriedade de dependência deve ser <xref:System.Windows.DependencyProperty.Name%2A> o que você escolheu para a propriedade de dependência como <xref:System.Windows.DependencyProperty.Register%2A> parte da chamada, acrescentada pela cadeia `Property`de caracteres literal. Por exemplo, se você registrar uma propriedade de dependência com <xref:System.Windows.DependencyProperty.Name%2A> um `Location`de, o campo identificador que você definir para a propriedade de dependência deverá ser `LocationProperty`nomeado.  
  
 Neste exemplo, o nome da propriedade de dependência e seu acessador CLR `State`é; o campo identificador `StateProperty`é; o tipo da propriedade é <xref:System.Boolean>; e o tipo que registra a propriedade de dependência `MyStateControl`é.  
  
 Se você não conseguir seguir esse padrão de nomenclatura, os designers poderão não relatar sua propriedade corretamente e determinados aspectos do aplicativo de estilo do sistema de propriedade poderão não se comportar conforme o esperado.  
  
 Também é possível especificar metadados padrão para uma propriedade de dependência. Esse exemplo registra o valor padrão da propriedade de dependência `State` como `false`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Para obter mais informações sobre como e por que implementar uma propriedade de dependência, em vez de apenas fazer backup de uma propriedade CLR com um campo privado, consulte [visão geral das propriedades de dependência](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Tópicos de instruções](properties-how-to-topics.md)

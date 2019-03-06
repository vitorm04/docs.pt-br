---
title: 'Como: Substituir metadados para uma propriedade de dependência'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
ms.openlocfilehash: 5d2d692984bef34569b2c4bb80c3fb072e4c3f79
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365874"
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Como: Substituir metadados para uma propriedade de dependência
Este exemplo mostra como substituir metadados de propriedade de dependência padrão que vem de uma classe herdada, chamando o <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> método e fornecendo metadados específicos do tipo.  
  
## <a name="example"></a>Exemplo  
 Definindo seu <xref:System.Windows.PropertyMetadata>, uma classe pode definir os comportamentos da propriedade de dependência, como seus padrão valor e propriedade sistema retornos de chamada. Muitas classes de propriedades de dependência já tem metadados padrão estabelecido como parte do processo de registro. Isso inclui as propriedades de dependência que fazem parte do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]. Uma classe que herda a propriedade de dependência por meio da herança de sua classe pode substituir os metadados originais para que as características da propriedade que podem ser alteradas por meio de metadados corresponderão a qualquer requisito específico de subclasse.  
  
 A substituição de metadados em uma propriedade de dependência deve ser realizada antes da propriedade que está sendo colocada em uso pelo sistema de propriedades (isso é igual ao momento em que instâncias específicas de objetos que registram a propriedade são instanciadas). Chamadas para <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> deve ser executada dentro de construtores estáticos do tipo que fornece a próprio como o `forType` parâmetro de <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Se você tentar alterar os metadados quando existem instâncias do tipo proprietário, isso não gerará exceções, mas resultará em comportamentos inconsistentes no sistema de propriedade. Além disso, metadados só podem ser substituído uma vez por tipo. Tentativas subsequentes de substituir os metadados no mesmo tipo gerarão uma exceção.  
  
 No exemplo a seguir, a classe personalizada `MyAdvancedStateControl` substitui os metadados fornecidos para `StateProperty` por `MyAdvancedStateControl` com os novos metadados de propriedade. Por exemplo, o valor padrão do `StateProperty` agora é `true` quando a propriedade é consultada em uma instância `MyAdvancedStateControl` recém construída.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.DependencyProperty>
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Tópicos de instruções](properties-how-to-topics.md)

---
title: 'Como: Adicionar um tipo de proprietário para uma propriedade de dependência'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401126"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Como: Adicionar um tipo de proprietário para uma propriedade de dependência
Este exemplo mostra como adicionar uma classe como um proprietário de uma propriedade de dependência registrado para um tipo diferente. Ao fazer isso, o leitor de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e o sistema de propriedade podem reconhecer a classe como um proprietário adicional da propriedade. Adicionar como proprietário opcionalmente permite que a classe de adição forneça os metadados específicos do tipo.  
  
 No exemplo a seguir, `StateProperty` é uma propriedade registrada pela classe `MyStateControl`. A classe `UnrelatedStateControl` se adiciona como um proprietário `StateProperty` do usando o <xref:System.Windows.DependencyProperty.AddOwner%2A> método, especificamente usando a assinatura que permite novos metadados para a propriedade de dependência como ela existe no tipo de adição. Observe que você deve fornecer acessadores de Common Language Runtime (CLR) para a propriedade semelhante ao exemplo mostrado no exemplo de [implementação de uma propriedade de dependência](how-to-implement-a-dependency-property.md) , bem como expor novamente o identificador de propriedade de dependência na classe que está sendo adicionada como proprietário.  
  
 Sem os wrappers, a propriedade de dependência ainda funcionaria a partir da perspectiva do <xref:System.Windows.DependencyObject.GetValue%2A> acesso <xref:System.Windows.DependencyObject.SetValue%2A>programático usando o ou o. Mas, normalmente, você deseja paralelizar esse comportamento de sistema de propriedades com os wrappers de propriedade CLR. Os wrappers facilitam a definição da propriedade de dependência de forma programática e tornam possível definir as propriedades como atributos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Para saber como substituir metadados padrão, consulte [Substituir metadados para uma propriedade de dependência](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Consulte também

- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)

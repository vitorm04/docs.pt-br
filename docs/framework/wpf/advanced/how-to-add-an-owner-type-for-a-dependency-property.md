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
ms.openlocfilehash: 03ffec87c98c88452aa8fde89c64646eaf48a8da
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369585"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Como: Adicionar um tipo de proprietário para uma propriedade de dependência
Este exemplo mostra como adicionar uma classe como um proprietário de uma propriedade de dependência registrado para um tipo diferente. Ao fazer isso, o leitor de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e o sistema de propriedade podem reconhecer a classe como um proprietário adicional da propriedade. Adicionar como proprietário opcionalmente permite que a classe de adição forneça os metadados específicos do tipo.  
  
 No exemplo a seguir, `StateProperty` é uma propriedade registrada pela classe `MyStateControl`. A classe `UnrelatedStateControl` adiciona a mesma como um proprietário do `StateProperty` usando o <xref:System.Windows.DependencyProperty.AddOwner%2A> método, especificamente usando a assinatura que permite novos metadados para a propriedade de dependência como ela existe no tipo de adição. Observe que você deve fornecer acessadores de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] para a propriedade semelhantes ao exemplo mostrado no exemplo o [Implemente uma propriedade de dependência](how-to-implement-a-dependency-property.md), bem como expor novamente o identificador de propriedade de dependência na classe que está sendo adicionado como proprietário.  
  
 Sem wrappers, a propriedade de dependência ainda funcionaria da perspectiva do uso do acesso programático <xref:System.Windows.DependencyObject.GetValue%2A> ou <xref:System.Windows.DependencyObject.SetValue%2A>. Mas, geralmente, você deseja corresponder esse comportamento de propriedade e sistema com os wrappers da propriedade [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. Os wrappers facilitam a definição da propriedade de dependência de forma programática e tornam possível definir as propriedades como atributos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Para saber como substituir metadados padrão, consulte [Substituir metadados para uma propriedade de dependência](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Consulte também
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)

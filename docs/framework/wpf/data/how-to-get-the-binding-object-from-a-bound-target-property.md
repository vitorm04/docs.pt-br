---
title: 'Como: Obter o objeto de associação de uma propriedade de destino associada'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965431"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Como: Obter o objeto de associação de uma propriedade de destino associada
Este exemplo mostra como obter o objeto de associação de uma propriedade de destino associada a dados.  
  
## <a name="example"></a>Exemplo  
 Você pode fazer o seguinte para obter o <xref:System.Windows.Data.Binding> objeto:  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> Você deve especificar a propriedade de dependência para a associação desejada porque é possível que mais de uma propriedade do objeto de destino esteja usando a associação de dados.  
  
 Como alternativa, você pode obter o <xref:System.Windows.Data.BindingExpression> e obter o valor <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> da propriedade.  
  
 Para obter o exemplo completo, consulte [exemplo de validação de associação](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
> Se sua associação for a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Se for um <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Se você não tiver certeza se a propriedade de destino está associada <xref:System.Windows.Data.Binding>usando um <xref:System.Windows.Data.MultiBinding>, um ou <xref:System.Windows.Data.PriorityBinding>um, você pode <xref:System.Windows.Data.BindingOperations>usar<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>..  
  
## <a name="see-also"></a>Consulte também

- [Criar uma associação no código](how-to-create-a-binding-in-code.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)

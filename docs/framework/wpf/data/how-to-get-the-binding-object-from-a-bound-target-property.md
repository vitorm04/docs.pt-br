---
title: Como obter o objeto de associação de uma propriedade de destino associada
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: cf2ddc93a7c46ee6956d2731a786289f64086360
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976428"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Como obter o objeto de associação de uma propriedade de destino associada
Este exemplo mostra como obter o objeto de associação de uma propriedade de destino associada a dados.

## <a name="example"></a>Exemplo
 Você pode fazer o seguinte para obter o objeto <xref:System.Windows.Data.Binding>:

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> Você deve especificar a propriedade de dependência para a associação desejada porque é possível que mais de uma propriedade do objeto de destino esteja usando a associação de dados.

 Como alternativa, você pode obter a <xref:System.Windows.Data.BindingExpression> e obter o valor da propriedade <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.

 Para obter o exemplo completo, consulte [exemplo de validação de associação](https://go.microsoft.com/fwlink/?LinkID=159972).

> [!NOTE]
> Se sua associação for uma <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>. Se for um <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>. Se você não tiver certeza se a propriedade de destino está associada usando uma <xref:System.Windows.Data.Binding>, uma <xref:System.Windows.Data.MultiBinding>ou uma <xref:System.Windows.Data.PriorityBinding>, você pode usar <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Consulte também

- [Criar uma associação no código](how-to-create-a-binding-in-code.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)

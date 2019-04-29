---
title: 'Como: Obter o objeto de associação de uma propriedade de destino associada'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7c7392bc11af57b2e9f27e2302f36efb59d40e9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933400"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Como: Obter o objeto de associação de uma propriedade de destino associada
Este exemplo mostra como obter o objeto de associação de uma propriedade de destino de associação de dados.  
  
## <a name="example"></a>Exemplo  
 Você pode fazer o seguinte para obter o <xref:System.Windows.Data.Binding> objeto:  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Você deve especificar a propriedade de dependência para a associação que desejar, pois é possível que mais de uma propriedade do objeto de destino está usando a associação de dados.  
  
 Como alternativa, você pode obter o <xref:System.Windows.Data.BindingExpression> e, em seguida, obter o valor da <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> propriedade.  
  
 Para um exemplo completo, consulte [exemplo de validação de associação](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Se a associação for um <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Se for um <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Se você não tiver certeza se a propriedade de destino está associada usando um <xref:System.Windows.Data.Binding>, um <xref:System.Windows.Data.MultiBinding>, ou uma <xref:System.Windows.Data.PriorityBinding>, você pode usar <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Consulte também

- [Criar uma associação no código](how-to-create-a-binding-in-code.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)

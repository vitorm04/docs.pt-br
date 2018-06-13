---
title: Como implementar PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: cf0ed5c2b55358d3a583ac89e307b23b3ab08a9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557752"
---
# <a name="how-to-implement-prioritybinding"></a>Como implementar PriorityBinding
<xref:System.Windows.Data.PriorityBinding> em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funciona especificando uma lista de associações. A lista de associações é ordenada da prioridade mais alta para a prioridade mais baixa. Se a associação de maior prioridade retornar um valor com êxito quando ele é processado, nunca haverá a necessidade de processar as outras associações na lista. Pode ser o caso de a associação de maior prioridade levar muito tempo para ser avaliada, a próxima prioridade mais alta que retorna um valor com sucesso será usada até que uma associação de uma prioridade mais alta retorne um valor com êxito.  
  
## <a name="example"></a>Exemplo  
 Para demonstrar como <xref:System.Windows.Data.PriorityBinding> funciona, o `AsyncDataSource` objeto foi criado com as seguintes três propriedades: `FastDP`, `SlowerDP`, e `SlowestDP`.  
  
 O acessador get de `FastDP` retorna o valor do membro de dados `_fastDP`.  
  
 O acessador get da `SlowerDP` aguarda três segundos antes de retornar o valor do membro de dados `_slowerDP`.  
  
 O acessador get da `SlowestDP` aguarda cinco segundos antes de retornar o valor do membro de dados `_slowestDP`.  
  
> [!NOTE]
>  Este exemplo tem fins apenas demonstrativos. As diretrizes de [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] recomendam não definir propriedades que são ordens de magnitude mais lentas do que seria um conjunto de campos. Para obter mais informações, consulte [NIB: escolhendo entre propriedades e métodos](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 O <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade associa o acima `AsyncDS` usando <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Quando o mecanismo de associação processa o <xref:System.Windows.Data.Binding> objetos, ele começa com a primeira <xref:System.Windows.Data.Binding>, que é associado a `SlowestDP` propriedade. Quando isso <xref:System.Windows.Data.Binding> é processado, ele não retorna um valor com êxito porque ele está em suspensão por 5 segundos, até o próximo <xref:System.Windows.Data.Binding> elemento é processado. A próxima <xref:System.Windows.Data.Binding> não retorna um valor com sucesso porque está dormindo por 3 segundos. O mecanismo de associação, em seguida, move para o próximo <xref:System.Windows.Data.Binding> elemento, que é associado a `FastDP` propriedade. Isso <xref:System.Windows.Data.Binding> retorna o valor "Fast Value". O <xref:System.Windows.Controls.TextBlock> agora mostra o valor "Fast Value".  
  
 Depois de 3 segundos, a propriedade `SlowerDP` retorna o valor “Valor mais Lento”. O <xref:System.Windows.Controls.TextBlock> , em seguida, exibe o valor "mais lento".  
  
 Depois de 5 segundos, a propriedade `SlowestDP` retorna o valor “Valor mais Lento”. Essa associação tem a maior prioridade porque é listada primeiro. O <xref:System.Windows.Controls.TextBlock> agora exibe o valor "mais lento".  
  
 Consulte <xref:System.Windows.Data.PriorityBinding> para obter informações sobre o que é considerado um valor de retorno com sucesso de uma associação.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

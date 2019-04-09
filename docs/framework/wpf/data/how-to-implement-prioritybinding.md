---
title: 'Como: Implementar PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: aaf2caff1e2684e08c7eb65125536f1070203d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207559"
---
# <a name="how-to-implement-prioritybinding"></a>Como: Implementar PriorityBinding
<xref:System.Windows.Data.PriorityBinding> no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funciona especificando uma lista de associações. A lista de associações é ordenada da prioridade mais alta para a prioridade mais baixa. Se a associação de maior prioridade retornar um valor com êxito quando ele é processado, nunca haverá a necessidade de processar as outras associações na lista. Pode ser o caso de a associação de maior prioridade levar muito tempo para ser avaliada, a próxima prioridade mais alta que retorna um valor com sucesso será usada até que uma associação de uma prioridade mais alta retorne um valor com êxito.  
  
## <a name="example"></a>Exemplo  
 Para demonstrar como <xref:System.Windows.Data.PriorityBinding> funcione, o `AsyncDataSource` objeto foi criado com as seguintes três propriedades: `FastDP`, `SlowerDP`, e `SlowestDP`.  
  
 O acessador get de `FastDP` retorna o valor do membro de dados `_fastDP`.  
  
 O acessador get da `SlowerDP` aguarda três segundos antes de retornar o valor do membro de dados `_slowerDP`.  
  
 O acessador get da `SlowestDP` aguarda cinco segundos antes de retornar o valor do membro de dados `_slowestDP`.  
  
> [!NOTE]
>  Este exemplo tem fins apenas demonstrativos. As diretrizes de [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] recomendam não definir propriedades que são ordens de magnitude mais lentas do que seria um conjunto de campos. Para obter mais informações, consulte [escolhendo entre propriedades e métodos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 O <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade associa ao acima `AsyncDS` usando <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Quando o mecanismo de associação processa o <xref:System.Windows.Data.Binding> objetos, ela começa com a primeira <xref:System.Windows.Data.Binding>, que é associado a `SlowestDP` propriedade. Quando isso <xref:System.Windows.Data.Binding> é processado, ele não retorna um valor com sucesso porque ele está suspenso por 5 segundos, portanto, a próxima <xref:System.Windows.Data.Binding> elemento é processado. A próxima <xref:System.Windows.Data.Binding> não retorna um valor com êxito porque ele está suspenso por 3 segundos. O mecanismo de associação, em seguida, move para a próxima <xref:System.Windows.Data.Binding> elemento, que é associado a `FastDP` propriedade. Isso <xref:System.Windows.Data.Binding> retorna o valor "Valor rápido". O <xref:System.Windows.Controls.TextBlock> agora mostra o valor "Valor rápido".  
  
 Depois de 3 segundos, a propriedade `SlowerDP` retorna o valor “Valor mais Lento”. O <xref:System.Windows.Controls.TextBlock> , em seguida, exibe o valor "Valor mais lento".  
  
 Depois de 5 segundos, a propriedade `SlowestDP` retorna o valor “Valor mais Lento”. Essa associação tem a maior prioridade porque é listada primeiro. O <xref:System.Windows.Controls.TextBlock> agora mostra o valor "Valor Lentíssimo".  
  
 Consulte <xref:System.Windows.Data.PriorityBinding> para obter informações sobre o que é considerado um valor de retorno bem-sucedido de uma associação.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos explicativos ](data-binding-how-to-topics.md)

---
title: Como implementar PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459787"
---
# <a name="how-to-implement-prioritybinding"></a>Como implementar PriorityBinding
<xref:System.Windows.Data.PriorityBinding> no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funciona especificando uma lista de associações. A lista de associações é ordenada da prioridade mais alta para a prioridade mais baixa. Se a associação de maior prioridade retornar um valor com êxito quando ele é processado, nunca haverá a necessidade de processar as outras associações na lista. Pode ser o caso de a associação de maior prioridade levar muito tempo para ser avaliada, a próxima prioridade mais alta que retorna um valor com sucesso será usada até que uma associação de uma prioridade mais alta retorne um valor com êxito.  
  
## <a name="example"></a>Exemplo  
 Para demonstrar como <xref:System.Windows.Data.PriorityBinding> funciona, o objeto `AsyncDataSource` foi criado com as três propriedades a seguir: `FastDP`, `SlowerDP`e `SlowestDP`.  
  
 O acessador get de `FastDP` retorna o valor do membro de dados `_fastDP`.  
  
 O acessador get da `SlowerDP` aguarda três segundos antes de retornar o valor do membro de dados `_slowerDP`.  
  
 O acessador get da `SlowestDP` aguarda cinco segundos antes de retornar o valor do membro de dados `_slowestDP`.  
  
> [!NOTE]
> Este exemplo tem fins apenas demonstrativos. As diretrizes do .NET recomendam a definição de propriedades que são ordens de magnitude mais lentas do que um conjunto de campos. Para obter mais informações, consulte [escolhendo entre propriedades e métodos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 A propriedade <xref:System.Windows.Controls.TextBlock.Text%2A> associa-se ao `AsyncDS` acima usando <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Quando o mecanismo de associação processa os objetos <xref:System.Windows.Data.Binding>, ele começa com a primeira <xref:System.Windows.Data.Binding>, que está associada à propriedade `SlowestDP`. Quando esse <xref:System.Windows.Data.Binding> é processado, ele não retorna um valor com êxito porque está em suspensão por 5 segundos, portanto, o próximo elemento de <xref:System.Windows.Data.Binding> é processado. A próxima <xref:System.Windows.Data.Binding> não retorna um valor com êxito porque está em suspensão por 3 segundos. Em seguida, o mecanismo de associação passa para o próximo elemento <xref:System.Windows.Data.Binding>, que está associado à propriedade `FastDP`. Essa <xref:System.Windows.Data.Binding> retorna o valor "Fast Value". O <xref:System.Windows.Controls.TextBlock> agora exibe o valor "Fast Value".  
  
 Depois de 3 segundos, a propriedade `SlowerDP` retorna o valor “Valor mais Lento”. O <xref:System.Windows.Controls.TextBlock> exibe o valor "valor mais lento".  
  
 Depois de 5 segundos, a propriedade `SlowestDP` retorna o valor “Valor mais Lento”. Essa associação tem a maior prioridade porque é listada primeiro. O <xref:System.Windows.Controls.TextBlock> agora exibe o valor "valor mais lento".  
  
 Consulte <xref:System.Windows.Data.PriorityBinding> para obter informações sobre o que é considerado um valor de retorno bem-sucedido de uma associação.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)

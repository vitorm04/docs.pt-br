---
title: 'Como: Implementar PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: ad19db9d686469e3ade1ff188553fceb8d525674
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937444"
---
# <a name="how-to-implement-prioritybinding"></a>Como: Implementar PriorityBinding
<xref:System.Windows.Data.PriorityBinding>no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Works, especificando uma lista de associações. A lista de associações é ordenada da prioridade mais alta para a prioridade mais baixa. Se a associação de maior prioridade retornar um valor com êxito quando ele é processado, nunca haverá a necessidade de processar as outras associações na lista. Pode ser o caso de a associação de maior prioridade levar muito tempo para ser avaliada, a próxima prioridade mais alta que retorna um valor com sucesso será usada até que uma associação de uma prioridade mais alta retorne um valor com êxito.  
  
## <a name="example"></a>Exemplo  
 Para demonstrar como <xref:System.Windows.Data.PriorityBinding> o funciona, `AsyncDataSource` o objeto foi criado com as três propriedades a seguir `FastDP`: `SlowerDP`, e `SlowestDP`.  
  
 O acessador get de `FastDP` retorna o valor do membro de dados `_fastDP`.  
  
 O acessador get da `SlowerDP` aguarda três segundos antes de retornar o valor do membro de dados `_slowerDP`.  
  
 O acessador get da `SlowestDP` aguarda cinco segundos antes de retornar o valor do membro de dados `_slowestDP`.  
  
> [!NOTE]
> Este exemplo tem fins apenas demonstrativos. As diretrizes de [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] recomendam não definir propriedades que são ordens de magnitude mais lentas do que seria um conjunto de campos. Para obter mais informações, consulte [escolhendo entre propriedades e métodos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 A <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade é vinculada ao anterior `AsyncDS` usando <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Quando o mecanismo de associação processa <xref:System.Windows.Data.Binding> os objetos, ele começa com o <xref:System.Windows.Data.Binding>primeiro, `SlowestDP` que está associado à propriedade. Quando isso <xref:System.Windows.Data.Binding> é processado, ele não retorna um valor com êxito porque está em suspensão por 5 segundos, portanto, o próximo <xref:System.Windows.Data.Binding> elemento é processado. O próximo <xref:System.Windows.Data.Binding> não retorna um valor com êxito porque está em suspensão por 3 segundos. Em seguida, o mecanismo de associação passa <xref:System.Windows.Data.Binding> para o próximo elemento, que está `FastDP` associado à propriedade. Isso <xref:System.Windows.Data.Binding> retorna o valor "Fast Value". O <xref:System.Windows.Controls.TextBlock> agora exibe o valor "Fast Value".  
  
 Depois de 3 segundos, a propriedade `SlowerDP` retorna o valor “Valor mais Lento”. <xref:System.Windows.Controls.TextBlock> Em seguida, exibe o valor "valor mais lento".  
  
 Depois de 5 segundos, a propriedade `SlowestDP` retorna o valor “Valor mais Lento”. Essa associação tem a maior prioridade porque é listada primeiro. O <xref:System.Windows.Controls.TextBlock> agora exibe o valor "valor mais lento".  
  
 Consulte <xref:System.Windows.Data.PriorityBinding> para obter informações sobre o que é considerado um valor de retorno bem-sucedido de uma associação.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)

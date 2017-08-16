---
title: "Mitigação: rolagem horizontal e virtualização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5bafd9b-a3b3-4f92-8241-2aad254fb1a9
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40eaf185e9c0c60493e9a2e5428c58b7463789fe
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-horizontal-scrolling-and-virtualization"></a>Mitigação: rolagem horizontal e virtualização
Essa alteração se aplica a um <xref:System.Windows.Controls.ItemsControl> que faz sua própria virtualização na direção ortogonal para a direção de rolagem principal. (O principal exemplo é um controle <xref:System.Windows.Controls.DataGrid> com <xref:System.Windows.Controls.DataGrid.EnableColumnVirtualization%2A> definido como `true`.)  O resultado de certas operações de rolagem horizontal foi alterado para produzir resultados mais intuitivo e análogos aos resultados de operações verticais comparáveis.  As operações específicas incluem **Rolar Aqui** e **Borda Direita**, para usar os nomes de menu obtidos clicando com o botão direito em uma barra de rolagem horizontal.  Ambas calculam um deslocamento de candidato e chamam <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>.  Depois de rolar para o novo deslocamento, a definição de "aqui" ou "borda direita" pode mudar, pois um conteúdo com virtualização removida recentemente alterou o valor de <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A?displayProperty=fullName>.  
  
## <a name="description-of-the-change"></a>Descrição da mudança  
 Antes do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a operação de rolagem simplesmente usava o deslocamento do candidato, embora isso talvez não seja mais "aqui" ou na "borda direita".  Isso resulta em efeitos de "salto" de rolagem, melhor ilustrado pelo exemplo.  Suponha que um controle <xref:System.Windows.Controls.DataGrid> tenha <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> definido como 1000 e <xref:System.Windows.FrameworkElement.Width%2A> definido como 200.  Uma rolagem para "Borda Direita" usa o deslocamento de candidato 1000-200 = 800.  Durante a rolagem até esse deslocamento, a virtualização de novas colunas é eliminada; vamos supor que elas sejam muito largas, então o <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> muda para 2000.  A rolagem termina com <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A>= 800 e "salta" de volta ao centro da barra de rolagem – precisamente em 800/2000 = 40%.  
  
 A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], um novo deslocamento candidato será recalculado quando essa situação ocorrer. (A rolagem vertical já funciona assim.)  
  
## <a name="impact"></a>Impacto  
 A alteração proporciona uma experiência mais previsível e intuitiva para o usuário final, mas também pode afetar qualquer aplicativo que dependa do valor exato de <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> após uma rolagem horizontal, seja ela invocada pelo usuário final ou por uma chamada explícita para <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>.  
  
## <a name="mitigation"></a>Redução  
 Um aplicativo que usa um valor previsto para <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> deve ser alterado para recuperar o valor real (e o valor de <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A>) após qualquer rolagem horizontal que poderia alterar <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> devido à eliminação da virtualização.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)


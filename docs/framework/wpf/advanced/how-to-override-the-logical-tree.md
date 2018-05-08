---
title: Como substituir a árvore lógica
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: 0c7269b9ea052019e2e4f6def23b063903cbb5e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-override-the-logical-tree"></a>Como substituir a árvore lógica
Embora não seja necessário na maioria dos casos, autores de controle avançados têm a opção de substituir a árvore lógica.  
  
## <a name="example"></a>Exemplo  
 Este exemplo descreve como subclasse <xref:System.Windows.Controls.StackPanel> para substituir a árvore lógica, nesse caso, para impor um comportamento que o painel somente pode ter e processará apenas um único elemento filho. Isso não é necessariamente um comportamento praticamente desejável, mas é mostrado aqui como um meio de que ilustra o cenário para substituir a árvore lógica normal de um elemento.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).

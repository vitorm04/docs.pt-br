---
title: 'Como: Substituir a árvore lógica'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768440"
---
# <a name="how-to-override-the-logical-tree"></a>Como: Substituir a árvore lógica
Embora não seja necessário na maioria dos casos, autores de controle avançados tem a opção de substituir a árvore lógica.  
  
## <a name="example"></a>Exemplo  
 Este exemplo descreve como subclasse <xref:System.Windows.Controls.StackPanel> para substituir a árvore lógica, nesse caso, para impor um comportamento que o painel pode ter somente e renderizará somente um único elemento filho. Isso não é necessariamente um comportamento praticamente desejável, mas é mostrado aqui como um meio de que ilustra o cenário para substituir a árvore lógica normal de um elemento.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](trees-in-wpf.md).

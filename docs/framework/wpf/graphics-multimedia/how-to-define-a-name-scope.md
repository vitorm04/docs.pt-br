---
title: 'Como: Definir um escopo de nome'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: a03f477dd31909e8cb9dde9cd29da6f38d665758
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904144"
---
# <a name="how-to-define-a-name-scope"></a>Como: Definir um escopo de nome
Para animar com <xref:System.Windows.Media.Animation.Storyboard> no código, você deve criar um <xref:System.Windows.NameScope> e registrar os nomes de objetos de destino com o elemento que possui esse escopo de nome. No exemplo a seguir, uma <xref:System.Windows.NameScope> é criado para `myMainPanel`. Dois botões, `button1` e `button2`, são adicionados ao painel e os nomes registrados. Várias animações e um <xref:System.Windows.Media.Animation.Storyboard> são criados. O storyboard <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método é usado para iniciar as animações.  
  
 Porque `button1`, `button2`, e `myMainPanel` compartilham o mesmo escopo de nome, qualquer um deles pode ser usado com o <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método para iniciar as animações.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>Consulte também

- [Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md)
- [Visão geral da animação](animation-overview.md)

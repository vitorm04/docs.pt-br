---
title: 'Como: Use com uma região de teste de clique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 1866810b875063271e206da1fe5d6fc06f7b5de0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564299"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>Como: Use com uma região de teste de clique
A finalidade de teste de clique é determinar se o cursor está sobre um determinado objeto, como um ícone ou um botão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma região em forma de sinal de adição, formando a união de duas regiões retangulares. Suponha que a variável `point` contém o local do clique mais recente. O código verifica para ver se `point` na região em forma de sinal de adição. Se o ponto está na região (uma ocorrência), a região é preenchida com um pincel vermelho opaco. Caso contrário, a região é preenchida com um pincel vermelho semitransparente.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.Region>
- [Regiões no GDI+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)
- [Como: Use com uma região de recorte](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)

---
title: "Como usar um teste de clique com uma região"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: adc55d137a5578dbe8649afa02ab8525d4913cd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-hit-testing-with-a-region"></a>Como usar um teste de clique com uma região
A finalidade de teste de clique é determinar se o cursor está sobre um determinado objeto, como um ícone ou um botão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma região em forma de adição formando a união de duas regiões retangulares. Suponha que a variável `point` contém o local do clique mais recente. O código verifica para ver se `point` na região em forma de adição. Se o ponto estiver na região (uma ocorrência), a região é preenchida com um pincel vermelho opaco. Caso contrário, a região é preenchida com um pincel vermelho semitransparente.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Region>  
 [Regiões no GDI+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Como Usar o Recorte com uma Região](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)

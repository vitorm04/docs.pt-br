---
title: Construtor &#39; &lt;nome&gt; &#39; não é possível chamar a mesmo
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 4a02277893147716098a3dcc327e221e0775d476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662719"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Construtor &#39; &lt;nome&gt; &#39; não é possível chamar a mesmo
Um `Sub New` procedimento em uma classe ou estrutura chama a mesmo.  
  
 A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ele é o primeiro é criado. Uma classe ou estrutura pode ter vários construtores, desde que todos eles tenham listas de parâmetros diferentes. Um construtor pode chamar outro construtor para executar sua funcionalidade, além de seu próprio. Mas não faz sentido para um construtor chamar a mesmo e, na verdade ele resultaria em recursão infinita se permitido.  
  
 **ID do erro:** BC30298  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a lista de parâmetros do construtor que está sendo chamado. Ele deve ser diferente do construtor fazendo a chamada.  
  
2.  Se você não pretende chamar um construtor diferente, remova o `Sub New` chamar inteiramente.  
  
## <a name="see-also"></a>Consulte também
- [Tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

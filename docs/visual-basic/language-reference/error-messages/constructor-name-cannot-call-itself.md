---
title: O construtor '<name>' não pode se chamar
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 67933e9365b1aa18063f0ccf3c2146a261e7eafc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276036"
---
# <a name="constructor-name-cannot-call-itself"></a>Construtor '\<nome >' não pode chamar a mesmo
Um `Sub New` procedimento em uma classe ou estrutura chama a mesmo.  
  
 A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ele é o primeiro é criado. Uma classe ou estrutura pode ter vários construtores, desde que todos eles tenham listas de parâmetros diferentes. Um construtor pode chamar outro construtor para executar sua funcionalidade, além de seu próprio. Mas não faz sentido para um construtor chamar a mesmo e, na verdade ele resultaria em recursão infinita se permitido.  
  
 **ID do erro:** BC30298  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a lista de parâmetros do construtor que está sendo chamado. Ele deve ser diferente do construtor fazendo a chamada.  
  
2.  Se você não pretende chamar um construtor diferente, remova o `Sub New` chamar inteiramente.  
  
## <a name="see-also"></a>Consulte também
- [Tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

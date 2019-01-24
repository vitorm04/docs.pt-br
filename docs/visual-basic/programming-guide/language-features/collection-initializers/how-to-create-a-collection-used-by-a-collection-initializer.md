---
title: 'Como: Criar uma coleção usada por um inicializador de coleção (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: aaa367e5a1739f26e9b0458d8f2fc44462b73b7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631718"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Como: Criar uma coleção usada por um inicializador de coleção (Visual Basic)
Quando você usa um inicializador de coleção para criar uma coleção, o compilador do Visual Basic procura um `Add` método de tipo de coleção para a qual os parâmetros para o `Add` método correspondem aos tipos dos valores no inicializador de coleção. Isso `Add` método é usado para popular a coleção com os valores do inicializador de coleção.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra uma `OrderCollection` coleção que contém uma pública `Add` método um inicializador de coleção pode usar para adicionar objetos do tipo `Order`. O `Add` método permite que você use a sintaxe do inicializador de coleção reduzida.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Inicializadores de Coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Como: Criar um método para Adicionar extensão usado por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

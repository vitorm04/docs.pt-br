---
title: 'Como: Criar uma coleção usada por um inicializador de coleção (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 75c280b57df03bde173c740123cccda278536dc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053620"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Como: Criar uma coleção usada por um inicializador de coleção (Visual Basic)
Quando você usa um inicializador de coleção para criar uma coleção, o compilador do Visual Basic procura um `Add` método de tipo de coleção para a qual os parâmetros para o `Add` método correspondem aos tipos dos valores no inicializador de coleção. Isso `Add` método é usado para popular a coleção com os valores do inicializador de coleção.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra uma `OrderCollection` coleção que contém uma pública `Add` método um inicializador de coleção pode usar para adicionar objetos do tipo `Order`. O `Add` método permite que você use a sintaxe do inicializador de coleção reduzida.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Inicializadores de Coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Como: Criar um método para Adicionar extensão usado por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

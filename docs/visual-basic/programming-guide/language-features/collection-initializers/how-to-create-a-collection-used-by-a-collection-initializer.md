---
title: Como criar uma coleção usada por um inicializador de coleção
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 5eaf9e828455bf2accda86ab52a1ce645f10b9ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349057"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Como criar uma coleção usada por um inicializador de coleção (Visual Basic)
Quando você usa um inicializador de coleção para criar uma coleção, o compilador Visual Basic procura um método `Add` do tipo de coleção para o qual os parâmetros do método `Add` correspondem aos tipos de valores no inicializador de coleção. Esse método de `Add` é usado para popular a coleção com os valores do inicializador de coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma coleção de `OrderCollection` que contém um método público `Add` que um inicializador de coleção pode usar para adicionar objetos do tipo `Order`. O método `Add` permite que você use a sintaxe de inicializador de coleção reduzida.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Inicializadores de Coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Como criar um método para adicionar extensão usado por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

---
title: Como criar uma coleção usada por um inicializador de coleção (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 6158b6f02d95260e2955e77d732fae8b8d9d5e04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654155"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Como criar uma coleção usada por um inicializador de coleção (Visual Basic)
Quando você usa um inicializador de coleção para criar uma coleção, o compilador do Visual Basic procura um `Add` método do tipo de coleção para a qual os parâmetros para o `Add` método correspondem aos tipos de valores em um inicializador de coleção. Isso `Add` método é usado para preencher a coleção com os valores do inicializador de coleção.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um `OrderCollection` coleção que contém um público `Add` método utilizado um inicializador de coleção para adicionar objetos do tipo `Order`. O `Add` método permite que você use a sintaxe do inicializador de coleção reduzido.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Inicializadores de Coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Como criar um método para adicionar extensão usado por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)

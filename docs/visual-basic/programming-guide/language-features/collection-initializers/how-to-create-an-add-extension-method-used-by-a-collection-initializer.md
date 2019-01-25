---
title: 'Como: Criar um método para Adicionar extensão usado por um inicializador de coleção (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 3a1db8ede8162b329d546c0e712ef1c2df7d7883
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661666"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Como: Criar um método para Adicionar extensão usado por um inicializador de coleção (Visual Basic)
Quando você usa um inicializador de coleção para criar uma coleção, o compilador do Visual Basic procura um `Add` método de tipo de coleção para a qual os parâmetros para o `Add` método correspondem aos tipos dos valores no inicializador de coleção. Isso `Add` método é usado para popular a coleção com os valores do inicializador de coleção.  
  
 Se nenhuma correspondência `Add` método existe e você não pode modificar o código para a coleção, você pode adicionar um método de extensão chamado `Add` que usa os parâmetros que são necessários para o inicializador de coleção. Isso normalmente é o que você precisa fazer ao usar inicializadores de coleção para coleções genéricas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar um método de extensão para o genérico <xref:System.Collections.Generic.List%601> tipo de forma que um inicializador de coleção pode ser usado para adicionar objetos do tipo `Employee`. O método de extensão permite que você use a sintaxe do inicializador de coleção reduzida.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Inicializadores de Coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Como: Criar uma coleção usada por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)

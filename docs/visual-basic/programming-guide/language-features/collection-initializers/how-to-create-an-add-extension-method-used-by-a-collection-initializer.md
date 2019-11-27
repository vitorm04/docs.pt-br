---
title: Como criar um método para adicionar extensão usado por um inicializador de coleção
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 6d5f9d38b413b79f111a14ec3829c57a9797ce54
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346721"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Como criar um método para adicionar extensão usado por um inicializador de coleção (Visual Basic)
Quando você usa um inicializador de coleção para criar uma coleção, o compilador Visual Basic procura um método `Add` do tipo de coleção para o qual os parâmetros do método `Add` correspondem aos tipos de valores no inicializador de coleção. Esse método de `Add` é usado para popular a coleção com os valores do inicializador de coleção.  
  
 Se nenhum método de `Add` correspondente existir e você não puder modificar o código para a coleção, você poderá adicionar um método de extensão chamado `Add` que usa os parâmetros exigidos pelo inicializador de coleção. Normalmente, isso é o que você precisa fazer quando usa inicializadores de coleção para coleções genéricas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar um método de extensão ao tipo de <xref:System.Collections.Generic.List%601> genérico para que um inicializador de coleção possa ser usado para adicionar objetos do tipo `Employee`. O método de extensão permite que você use a sintaxe de inicializador de coleção abreviada.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Inicializadores de Coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Como criar uma coleção usada por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)

---
title: "Como: criar um método para Adicionar extensão usado por um inicializador de coleção (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 15cc2745d971b4eafddb623c736f76a7b1907074
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Como criar um método para adicionar extensão usado por um inicializador de coleção (Visual Basic)
Quando você usa um inicializador de coleção para criar uma coleção, o compilador do Visual Basic procura um `Add` método do tipo de coleção para a qual os parâmetros para o `Add` método correspondem aos tipos de valores no inicializador de coleção. Isso `Add` método é usado para preencher a coleção com os valores do inicializador de coleção.  
  
 Se nenhuma correspondência `Add` método existe e não é possível modificar o código para a coleção, você pode adicionar um método de extensão chamado `Add` que usa os parâmetros necessários para o inicializador de coleção. Isso normalmente é o que você precisa fazer quando você usa os inicializadores de coleção para coleções genéricas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar um método de extensão para genérica <xref:System.Collections.Generic.List%601>tipo de forma que um inicializador de coleção pode ser usado para adicionar objetos do tipo `Employee`.</xref:System.Collections.Generic.List%601> O método de extensão permite que você use a sintaxe do inicializador de coleção reduzido.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1 n º&1;](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1 n º&2;](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1 n º&3;](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Inicializadores de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [Como criar uma coleção usada por um inicializador de coleção](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)

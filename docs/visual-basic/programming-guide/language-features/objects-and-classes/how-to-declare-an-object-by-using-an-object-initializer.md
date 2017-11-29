---
title: Como declarar um objeto usando um inicializador de objeto (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c818765cbeac7a3080ee666d464052493e5bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Como declarar um objeto usando um inicializador de objeto (Visual Basic)
Inicializadores de objeto permitem que você declarar e criar uma instância de uma classe em uma única instrução. Além disso, você pode inicializar um ou mais membros da instância ao mesmo tempo, sem chamar um construtor com parâmetros.  
  
 Quando você usa um inicializador de objeto para criar uma instância de um tipo nomeado, o construtor padrão para a classe é chamado, seguido pela inicialização dos membros designados na ordem que você especifica.  
  
 O procedimento a seguir mostra como criar uma instância de um `Student` classe de três maneiras diferentes. A classe tem nome, sobrenome e propriedades da classe ano, entre outros. Cada uma das três declarações cria uma nova instância da `Student`, com a propriedade `First` definida como "Michael", propriedade `Last` definida como "Terra", e todos os outros membros definidos com seus valores padrão. O resultado de cada declaração no procedimento é equivalente ao exemplo a seguir, que não usa um inicializador de objeto.  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 Para uma implementação de `Student` de classe, consulte [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Você pode copiar o código daquele tópico para configurar a classe e criar uma lista de `Student` objetos para trabalhar com.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Para criar um objeto de uma classe nomeada usando um inicializador de objeto  
  
1.  Comece a declaração como se você planejar usar um construtor.  
  
     `Dim student1 As New Student`  
  
2.  Digite a palavra-chave `With`, seguido por uma lista de inicialização entre chaves.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  Na lista de inicialização, inclua cada propriedade que você deseja inicializar e atribua um valor inicial a ela. O nome da propriedade é precedido por um período.  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     Você pode inicializar um ou mais membros da classe.  
  
4.  Como alternativa, você pode declarar uma nova instância da classe e, em seguida, atribuir um valor a ele. Primeiro, declarar uma instância de `Student`:  
  
     `Dim student2 As Student`  
  
5.  Começar a criação de uma instância de `Student` da maneira normal.  
  
     `Dim student2 As Student = New Student`  
  
6.  Tipo `With` e, em seguida, um inicializador de objeto para inicializar um ou mais membros da nova instância.  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  Você pode simplificar a definição na etapa anterior omitindo `As Student`. Se você fizer isso, o compilador determina que `student3` é uma instância de `Student` usando inferência de tipo local.  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     Para obter mais informações, consulte [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Consulte também  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Como criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [Inicializadores de objeto: tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

---
title: 'Como: Declarar um objeto usando um inicializador de objeto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 850e20fe8b5b6bfd392c80c87950a81a1a8a5c24
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755203"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Como: Declarar um objeto usando um inicializador de objeto (Visual Basic)
Inicializadores de objeto permitem que você declarar e instanciar uma instância de uma classe em uma única instrução. Além disso, você pode inicializar um ou mais membros da instância ao mesmo tempo, sem chamar um construtor com parâmetros.  
  
 Quando você usa um inicializador de objeto para criar uma instância de um tipo nomeado, o construtor sem parâmetros para a classe é chamado, seguido pela inicialização dos membros designados na ordem em que você especificar.  
  
 O procedimento a seguir mostra como criar uma instância de um `Student` classe de três maneiras diferentes. A classe tem nome, sobrenome e propriedades de ano de classe, entre outros. Cada uma das três declarações cria uma nova instância da `Student`, com a propriedade `First` definida como "Michael," propriedade `Last` definida como "Tucker", e todos os outros membros definidos para seus valores padrão. O resultado de cada declaração no procedimento é equivalente ao exemplo a seguir, que não usa um inicializador de objeto.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Para a implementação do `Student` classe, consulte [como: Criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Você pode copiar o código daquele tópico para configurar a classe e criar uma lista de `Student` objetos para trabalhar com.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Para criar um objeto de uma classe nomeada usando um inicializador de objeto  
  
1. Inicie a declaração como se planejar usar um construtor.  
  
     `Dim student1 As New Student`  
  
2. Digite a palavra-chave `With`, seguido por uma lista de inicialização entre chaves.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. Na lista de inicialização, inclua cada propriedade que você deseja inicializar e atribuir um valor inicial a ela. O nome da propriedade é precedido por um período.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Você pode inicializar um ou mais membros da classe.  
  
4. Como alternativa, você pode declarar uma nova instância da classe e, em seguida, atribuir um valor a ela. Em primeiro lugar, declarar uma instância de `Student`:  
  
     `Dim student2 As Student`  
  
5. Começar a criação de uma instância de `Student` da maneira normal.  
  
     `Dim student2 As Student = New Student`  
  
6. Tipo `With` e, em seguida, um inicializador de objeto para inicializar um ou mais membros da nova instância.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Você pode simplificar a definição na etapa anterior, omitindo `As Student`. Se você fizer isso, o compilador determina que `student3` é uma instância de `Student` usando inferência de tipo local.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Para obter mais informações, consulte [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Consulte também

- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Como: Criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [Inicializadores de objeto: Tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

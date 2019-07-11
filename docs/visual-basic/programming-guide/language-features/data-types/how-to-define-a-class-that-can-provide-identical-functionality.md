---
title: 'Como: Definir uma classe que pode fornecer uma funcionalidade idêntica em tipos de dados diferentes (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 19988e766d0f9ec895a24dddfcd17d0854aaf8ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757401"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Como: Definir uma classe que pode fornecer uma funcionalidade idêntica em tipos de dados diferentes (Visual Basic)
Você pode definir uma classe da qual você pode criar objetos que fornecem uma funcionalidade idêntica em tipos de dados diferentes. Para fazer isso, você especifica um ou mais *parâmetros de tipo* na definição. A classe, em seguida, pode servir como um modelo para objetos que usam vários tipos de dados. Uma classe definida dessa maneira é chamada um *classe genérica*.  
  
 A vantagem de definir uma classe genérica é que você define apenas uma vez, e seu código pode usá-lo para criar vários objetos que usam uma ampla variedade de tipos de dados. Isso resulta em desempenho melhor do que a definição de classe com o `Object` tipo.  
  
 Além das classes, você também pode definir e usar delegados, interfaces, procedimentos e estruturas genéricas.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Para definir uma classe com um parâmetro de tipo  
  
1. Defina a classe da forma normal.  
  
2. Adicione `(Of` *typeparameter* `)` imediatamente após o nome de classe para especificar um parâmetro de tipo.  
  
3. Se você tiver mais de um parâmetro de tipo, faça uma lista separada por vírgulas dentro dos parênteses. Não se repetem o `Of` palavra-chave.  
  
4. Se seu código executa operações em um parâmetro de tipo diferente de atribuição simples, siga esse parâmetro de tipo com uma `As` cláusula para adicionar um ou mais *restrições de*. Uma restrição garante que o tipo fornecido para esse parâmetro de tipo satisfaz um requisito, como o seguinte:  
  
    - Oferece suporte a uma operação, como `>`, que executa o código  
  
    - Dá suporte a um membro, como um método, que acessa seu código  
  
    - Expõe um construtor sem parâmetros  
  
     Se você não especificar quaisquer restrições, operações e membros que seu código pode usar somente são aquelas com suporte a [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md). Para obter mais informações, consulte [lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5. Identifique cada membro da classe que deve ser declarado com um tipo fornecido e declará-la `As` `typeparameter`. Isso se aplica ao armazenamento interno, parâmetros de procedimento e valores de retorno.  
  
6. Certifique-se de que seu código usa somente operações e métodos que são suportados por qualquer tipo de dados que ele pode fornecer a `itemType`.  
  
     O exemplo a seguir define uma classe que gerencia uma lista muito simples. Ele contém a lista da matriz interna `items`e o usando o código pode declarar o tipo de dados dos elementos de lista. Um construtor parametrizado permite o uso de código para definir o limite superior de `items`, e o construtor sem parâmetro define isso como 9 (para um total de 10 itens).  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     Você pode declarar uma classe de `simpleList` para manter uma lista de `Integer` valores, outra classe para conter uma lista de `String` valores e outra para conter `Date` valores. Com exceção do tipo de dados dos membros da lista, objetos criados a partir de todas essas classes têm comportamento idêntico.  
  
     O argumento de tipo que o código usado fornece ao `itemType` pode ser um tipo intrínseco, como `Boolean` ou `Double`, uma estrutura, uma enumeração ou qualquer tipo de classe, incluindo um que define seu aplicativo.  
  
     Você pode testar a classe `simpleList` com o código a seguir.  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Componentes de independência de linguagem e componentes independentes da linguagem](../../../../standard/language-independence-and-language-independent-components.md)
- [Of](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Lista de Tipos](../../../../visual-basic/language-reference/statements/type-list.md)
- [Como: usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)

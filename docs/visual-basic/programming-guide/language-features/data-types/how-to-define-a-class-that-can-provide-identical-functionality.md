---
title: Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes
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
ms.openlocfilehash: d80623d9e55358d37aa45f11f1525c80a09b91a6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350048"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes (Visual Basic)
Você pode definir uma classe na qual é possível criar objetos que fornecem funcionalidade idêntica em diferentes tipos de dados. Para fazer isso, você deve especificar um ou mais *parâmetros de tipo* na definição. A classe pode servir como um modelo para objetos que usam vários tipos de dados. Uma classe definida dessa maneira é chamada de *classe genérica*.  
  
 A vantagem de definir uma classe genérica é que você a define apenas uma vez, e seu código pode usá-la para criar vários objetos que usam uma ampla variedade de tipos de dados. Isso resulta em um melhor desempenho do que definir a classe com o tipo de `Object`.  
  
 Além das classes, você também pode definir e usar estruturas genéricas, interfaces, procedimentos e delegados.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Para definir uma classe com um parâmetro de tipo  
  
1. Defina a classe da maneira normal.  
  
2. Adicione `(Of` *typeparameter*`)` imediatamente após o nome da classe para especificar um parâmetro de tipo.  
  
3. Se você tiver mais de um parâmetro de tipo, crie uma lista separada por vírgulas dentro dos parênteses. Não repita a palavra-chave `Of`.  
  
4. Se o seu código executar operações em um parâmetro de tipo diferente de atribuição simples, siga esse parâmetro de tipo com uma cláusula `As` para adicionar uma ou mais *restrições*. Uma restrição garante que o tipo fornecido para esse parâmetro de tipo atenda a um requisito, como o seguinte:  
  
    - Dá suporte a uma operação, como `>`, que seu código executa  
  
    - Dá suporte a um membro, como um método, que seu código acessa  
  
    - Expõe um construtor sem parâmetros  
  
     Se você não especificar nenhuma restrição, as únicas operações e membros que seu código pode usar são aquelas com suporte pelo [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md). Para obter mais informações, consulte [lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5. Identifique cada membro de classe que deve ser declarado com um tipo fornecido e declare-o `As` `typeparameter`. Isso se aplica ao armazenamento interno, aos parâmetros de procedimento e aos valores de retorno.  
  
6. Certifique-se de que seu código usa apenas operações e métodos com suporte de qualquer tipo de dados que possa fornecer a `itemType`.  
  
     O exemplo a seguir define uma classe que gerencia uma lista muito simples. Ele contém a lista na matriz interna `items`e o uso do código pode declarar o tipo de dados dos elementos da lista. Um construtor com parâmetros permite que o código de uso defina o limite superior de `items`, e o construtor sem parâmetros define isso como 9 (para um total de 10 itens).  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     Você pode declarar uma classe de `simpleList` para manter uma lista de valores de `Integer`, outra classe para manter uma lista de valores de `String` e outra para conter `Date` valores. Exceto para o tipo de dados dos membros da lista, os objetos criados a partir de todas essas classes se comportam de forma idêntica.  
  
     O argumento de tipo que o código usando fornece a `itemType` pode ser um tipo intrínseco, como `Boolean` ou `Double`, uma estrutura, uma enumeração ou qualquer tipo de classe, incluindo um que seu aplicativo define.  
  
     Você pode testar a classe `simpleList` com o código a seguir.  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Componentes de independência de linguagem e componentes independentes da linguagem](../../../../standard/language-independence-and-language-independent-components.md)
- [Of](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Lista de Tipos](../../../../visual-basic/language-reference/statements/type-list.md)
- [Como usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)

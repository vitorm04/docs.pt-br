---
title: "Como: definir uma classe que pode fornecer funcionalidade idêntica em tipos de dados diferentes (Visual Basic) | Documentos do Microsoft"
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
- data type arguments, using
- type parameters, defining
- data type arguments, defining
- arguments [Visual Basic], data types
- Of keyword, using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters, using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters, type
- type arguments
- types [Visual Basic], generic
- parameters, generic
- type parameters
- data type arguments
- parameters, data type
- generics [Visual Basic], defining generic types
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a25b18f7467763e514c7f285ffe7d1edbd7f61f7
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes (Visual Basic)
Você pode definir uma classe da qual você pode criar objetos que fornecem funcionalidade idêntica em tipos de dados diferentes. Para fazer isso, você especifica um ou mais *parâmetros de tipo* na definição. A classe, em seguida, pode servir como um modelo para objetos que usam vários tipos de dados. Uma classe definida dessa maneira é chamada uma *classe genérica*.  
  
 A vantagem de definir uma classe genérica é que você define apenas uma vez, e seu código pode usá-lo para criar vários objetos que usam uma grande variedade de tipos de dados. Isso resulta em um desempenho melhor que a definição de classe com o `Object` tipo.  
  
 Além de classes, você também pode definir e usar delegados, interfaces, procedimentos e estruturas genéricas.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Para definir uma classe com um parâmetro de tipo  
  
1.  Defina a classe da forma normal.  
  
2.  Adicionar `(Of` *typeparameter* `)` imediatamente após o nome da classe para especificar um parâmetro de tipo.  
  
3.  Se você tiver mais de um parâmetro de tipo, faça uma lista separada por vírgulas dentro dos parênteses. Não se repetem o `Of` palavra-chave.  
  
4.  Se seu código executa operações em um parâmetro de tipo diferente de atribuição simples, siga esse parâmetro do tipo com uma `As` cláusula para adicionar um ou mais *restrições*. Uma restrição garante que o tipo fornecido para esse parâmetro do tipo satisfaça um requisito, como o seguinte:  
  
    -   Oferece suporte a uma operação, como `>`, que executa o código  
  
    -   Oferece suporte a um membro, como um método, que seu código acessa  
  
    -   Expõe um construtor sem parâmetros  
  
     Se você não especificar quaisquer restrições, operações e membros que seu código pode usar somente são aquelas com suporte a [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md). Para obter mais informações, consulte [tipo lista](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5.  Identifique cada membro da classe que será declarado com um tipo fornecido e declare- `As` `typeparameter`. Isso se aplica a armazenamento interno, parâmetros de procedimento e valores de retorno.  
  
6.  Certifique-se de que seu código use somente operações e métodos que são suportados por qualquer tipo de dados pode ele fornecer a `itemType`.  
  
     O exemplo a seguir define uma classe que gerencia uma lista muito simples. Ele contém a lista da matriz interna `items`e o uso de código pode declarar o tipo de dados dos elementos de lista. Um construtor parametrizado permite o uso de código para definir o limite superior de `items`, e o construtor padrão define esta como 9 (para um total de 10 itens).  
  
     [!code-vb[VbVbalrDataTypes&#7;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     Você pode declarar uma classe de `simpleList` para manter uma lista de `Integer` valores, outra classe para conter uma lista de `String` valores e outra para conter `Date` valores. Exceto pelo tipo de dados dos membros da lista, objetos criados a partir de todas essas classes tenham comportamento idêntico.  
  
     O argumento de tipo que o código usado fornece para `itemType` pode ser um tipo intrínseco como `Boolean` ou `Double`, uma estrutura, uma enumeração ou qualquer tipo de classe, inclusive uma que seu aplicativo define.  
  
     Você pode testar a classe `simpleList` com o código a seguir.  
  
     [!code-vb[VbVbalrDataTypes n º&8;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3)   
 [De](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md)   
 [Como: usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)

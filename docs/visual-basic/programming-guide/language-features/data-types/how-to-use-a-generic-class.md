---
title: 'Como: Usar uma classe genérica (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: e7d35a900ef4309963ff9de0ea77a12fd4577f12
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969668"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Como: Usar uma classe genérica (Visual Basic)
Uma classe que leva *parâmetros de tipo* é chamado um *classe genérica*. Se você estiver usando uma classe genérica, você pode gerar uma *classe construída* dele, fornecendo uma *argumento de tipo* para cada um desses parâmetros. Em seguida, você pode declarar uma variável do tipo de classe construído, e você pode criar uma instância da classe construída e atribuí-lo para a variável.  
  
 Além das classes, você também pode definir e usar delegados, interfaces, procedimentos e estruturas genéricas.  
  
 O procedimento a seguir usa uma classe genérica definida no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e cria uma instância dele.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Para usar uma classe que usa um parâmetro de tipo  
  
1.  No início do seu arquivo de origem, inclua uma [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para importar o <xref:System.Collections.Generic?displayProperty=nameWithType> namespace. Isso permite que você consulte os <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> classe sem precisar qualificar totalmente para diferenciá-lo de outras classes de consulta, como <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2.  Crie o objeto da maneira normal, mas adicione `(Of type)` imediatamente após o nome da classe.  
  
     O exemplo a seguir usa a mesma classe (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) para criar dois objetos de fila que mantêm itens de diferentes tipos de dados. Ele adiciona itens ao final de cada fila e, em seguida, remove e exibe os itens da frente de cada fila.  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Componentes de independência de linguagem e componentes independentes da linguagem](../../../../standard/language-independence-and-language-independent-components.md)
- [Of](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Instrução Imports (Tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Como: definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Iteradores](../../../../visual-basic/programming-guide/concepts/iterators.md)

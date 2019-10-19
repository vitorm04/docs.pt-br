---
title: Tipos de valor e referência
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582644"
---
# <a name="value-types-and-reference-types"></a>Tipos de valor e referência
Há dois tipos de tipo em Visual Basic: tipos de referência e tipos de valor. Variáveis de tipos de referência armazenam referências em seus dados (objetos) enquanto que variáveis de tipos de valor contém diretamente seus dados. Com tipos de referência, duas variáveis podem fazer referência ao mesmo objeto; portanto, operações em uma variável podem afetar o objeto referenciado pela outra variável. Com tipos de valor, cada variável tem sua própria cópia dos dados e não é possível que as operações em uma variável afetem a outra (exceto no caso do [modificador ByRef nos parâmetros](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Tipos de valor  
 Um tipo de dados é um *tipo de valor* se ele mantém os dados dentro de sua própria alocação de memória. Os tipos de valor incluem o seguinte:  
  
- Todos os tipos de dados numéricos  
  
- `Boolean`, `Char` e `Date`  
  
- Todas as estruturas, mesmo que seus membros sejam tipos de referência  
  
- As enumerações, já que seu tipo subjacente é sempre `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` ou `ULong`  
  
 Cada estrutura é um tipo de valor, mesmo que contenha membros de tipo de referência. Por esse motivo, tipos de valor como `Char` e `Integer` são implementados por estruturas de .NET Framework.  
  
 Você pode declarar um tipo de valor usando a palavra-chave reservada, por exemplo, `Decimal`. Você também pode usar a palavra-chave `New` para inicializar um tipo de valor. Isso é especialmente útil se o tipo tiver um construtor que aceite parâmetros. Um exemplo disso é o Construtor <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>, que cria um novo valor de `Decimal` a partir das partes fornecidas.  
  
## <a name="reference-types"></a>Tipos de referência  
 Um *tipo de referência* armazena uma referência a seus dados. Os tipos de referência incluem o seguinte:  
  
- `String`  
  
- Todas as matrizes, mesmo que seus elementos sejam de tipos de valor  
  
- Tipos de classe, como <xref:System.Windows.Forms.Form>  
  
- Delegados  
  
 Uma classe é um *tipo de referência*. Observe que cada matriz é um tipo de referência, mesmo que seus membros sejam de tipos de valor.  
  
 Como cada tipo de referência representa uma classe de .NET Framework subjacente, você deve usar a palavra-chave [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) ao inicializá-la. A instrução a seguir inicializa uma matriz.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Elementos que não são tipos  
 Os seguintes elementos de programação não se qualificam como tipos, porque você não pode especificar nenhum deles como um tipo de dados para um elemento declarado:  
  
- Namespaces  
  
- Módulos  
  
- Eventos  
  
- Propriedades e procedimentos  
  
- Variáveis, constantes e campos  
  
## <a name="working-with-the-object-data-type"></a>Trabalhando com o tipo de dados Object  
 Você pode atribuir um tipo de referência ou um tipo de valor a uma variável do tipo de dados `Object`. Uma variável `Object` sempre mantém uma referência aos dados, nunca os dados em si. No entanto, se você atribuir um tipo de valor a uma variável `Object`, ela se comporta como se ela contiver seus próprios dados. Para obter mais informações, consulte [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Você pode descobrir se uma variável `Object` está agindo como um tipo de referência ou um tipo de valor passando-a para o método <xref:Microsoft.VisualBasic.Information.IsReference%2A> na classe <xref:Microsoft.VisualBasic.Information> do namespace <xref:Microsoft.VisualBasic?displayProperty=nameWithType>. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> retornará `True` se o conteúdo da variável `Object` representar um tipo de referência.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Valor Anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Uso Eficiente de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)

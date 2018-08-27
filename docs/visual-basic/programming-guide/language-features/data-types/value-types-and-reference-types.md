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
ms.openlocfilehash: 9456316f71a213905bcb50336533c4e618f5174a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934179"
---
# <a name="value-types-and-reference-types"></a>Tipos de valor e referência
No Visual Basic, os tipos de dados são implementados com base em sua classificação. Os tipos de dados do Visual Basic podem ser classificados de acordo com se uma variável de um determinado tipo armazena seus próprios dados ou um ponteiro para os dados. Se ela armazena seus próprios dados é um *tipo de valor*; se ele contém um ponteiro para dados em outro lugar na memória é um *tipo de referência*.  
  
## <a name="value-types"></a>Tipos de valor  
 Um tipo de dados é um *tipo de valor* se ele contém os dados dentro de sua própria alocação de memória. Tipos de valor incluem o seguinte:  
  
-   Todos os tipos de dados numéricos  
  
-   `Boolean`, `Char` e `Date`  
  
-   Todas as estruturas, mesmo se seus membros são tipos de referência  
  
-   Enumerações, pois seu tipo subjacente é sempre `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, ou `ULong`  
  
 Cada estrutura é um tipo de valor, mesmo que ele contenha membros de tipo de referência. Por esse motivo, tipos de valor, tal como `Char` e `Integer` são implementados por estruturas do .NET Framework.  
  
 Você pode declarar um tipo de valor usando a palavra-chave reservada, por exemplo, `Decimal`. Você também pode usar o `New` palavra-chave para inicializar um tipo de valor. Isso é especialmente útil se o tipo tem um construtor que aceita parâmetros. Um exemplo disso é o <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> construtor, que cria um novo `Decimal` valor a partir das partes fornecidas.  
  
## <a name="reference-types"></a>Tipos de referência  
 Um *tipo de referência* contém um ponteiro para outro local da memória que contém os dados. Tipos de referência incluem o seguinte:  
  
-   `String`  
  
-   Todas as matrizes, mesmo se seus elementos são tipos de valor  
  
-   Tipos de classe, como <xref:System.Windows.Forms.Form>  
  
-   Delegados  
  
 Uma classe é um *tipo de referência*. Por esse motivo, tipos de referência, como `Object` e `String` são compatíveis com [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes. Observe que cada matriz é um tipo de referência, mesmo se seus membros são tipos de valor.  
  
 Como cada tipo de referência representa uma classe base do .NET Framework, você deve usar o [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave quando inicializá-la. A instrução a seguir inicializa uma matriz.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Elementos que não são de tipos  
 Os seguintes elementos de programação não se qualificam como tipos, porque você não pode especificar qualquer um deles como um tipo de dados para um elemento declarado:  
  
-   Namespaces  
  
-   Módulos  
  
-   Eventos  
  
-   Propriedades e procedimentos  
  
-   Variáveis, constantes e campos  
  
## <a name="working-with-the-object-data-type"></a>Trabalhando com o tipo de dados de objeto  
 Você pode atribuir um tipo de referência ou um tipo de valor a uma variável do `Object` tipo de dados. Um `Object` variável sempre contém um ponteiro para os dados, nunca os dados em si. No entanto, se você atribuir um tipo de valor para um `Object` variável, ele se comporta como se ele contém seus próprios dados. Para obter mais informações, consulte [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Você pode descobrir se um `Object` variável está atuando como um tipo de referência ou um tipo de valor, passando-o para o <xref:Microsoft.VisualBasic.Information.IsReference%2A> método na <xref:Microsoft.VisualBasic.Information> classe do <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Retorna `True` se o conteúdo a `Object` variável representa um tipo de referência.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Valor Anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Uso Eficiente de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)

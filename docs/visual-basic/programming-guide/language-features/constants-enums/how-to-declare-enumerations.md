---
title: Como declarar enumerações (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: e2dbdbbf6bf7fe3e4b71cbe7edc7a19b18f96ef2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Como declarar enumerações (Visual Basic)
Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou um módulo. Você não pode declarar uma enumeração dentro de um método. Para especificar o nível apropriado de acesso, use `Private`, `Protected`, `Friend`, ou `Public`.  
  
 Um `Enum` tipo tem um nome, um tipo subjacente e um conjunto de campos, cada uma representando uma constante. O nome deve ser um qualificador válido do Visual Basic .NET. O tipo subjacente deve ser um dos tipos de inteiro —`Byte`, `Short`, `Long` ou `Integer`. `Integer` é o padrão. Enumerações são sempre fortemente tipadas e não são intercambiáveis com tipos de número inteiro.  
  
 Enumerações não podem ter valores de ponto flutuante. Se uma enumeração é atribuída um valor de ponto flutuante com `Option Strict On`, um erro de compilação acontece. Se `Option Strict` é `Off`, o valor é convertido automaticamente para o `Enum` tipo.  
  
 Para obter informações sobre nomes e como usar o `Imports` instrução para garantir a qualificação de nome desnecessário, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Para declarar uma enumeração  
  
1.  Escreva uma declaração que inclui um nível de acesso do código, o `Enum` palavra-chave e um nome válido, como nos exemplos a seguir, cada uma delas declara outra `Enum`.  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  Defina as constantes na enumeração. Por padrão, a primeira constante em uma enumeração é inicializada como `0`, e as constantes subsequentes são inicializadas com um valor de constante anterior mais um. Por exemplo, a enumeração seguir `Days`, contém uma constante chamada `Sunday` com o valor `0`, uma constante chamada `Monday` com o valor `1`, uma constante chamada `Tuesday` com o valor de `2`, e assim por diante.  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  Explicitamente, você pode atribuir valores às constantes em uma enumeração usando uma instrução de atribuição. Você pode atribuir qualquer valor inteiro, incluindo números negativos. Por exemplo, talvez você queira constantes com valores menores que zero para representar condições de erro. Na enumeração seguir, a constante `Invalid` explicitamente atribuído o valor `–1`e a constante `Sunday` é atribuído o valor `0`. Porque é a primeira constante na enumeração, `Saturday` também é inicializada com o valor `0`. O valor de `Monday` é `1` (mais do que o valor de um `Sunday`); o valor de `Tuesday` é `2`, e assim por diante.  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Para declarar uma enumeração como um tipo explícito  
  
-   Especifique o tipo de enum usando o `As` cláusula, conforme mostrado no exemplo a seguir.  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Como: iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Visão Geral de Constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)

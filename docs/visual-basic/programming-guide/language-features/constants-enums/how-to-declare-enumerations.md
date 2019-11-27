---
title: 'Como: declarar enumerações'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 042aea045313bcaf3832274acf1000f87a084b72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354054"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Como declarar enumerações (Visual Basic)
Você cria uma enumeração com a instrução `Enum` na seção declarações de uma classe ou módulo. Você não pode declarar uma enumeração dentro de um método. Para especificar o nível apropriado de acesso, use `Private`, `Protected`, `Friend`ou `Public`.  
  
 Um tipo de `Enum` tem um nome, um tipo subjacente e um conjunto de campos, cada um representando uma constante. O nome deve ser um qualificador de Visual Basic .NET válido. O tipo subjacente deve ser um dos tipos inteiros:`Byte`, `Short`, `Long` ou `Integer`. `Integer` é o padrão. As enumerações são sempre fortemente tipadas e não são intercambiáveis com tipos de números inteiros.  
  
 Enumerações não podem ter valores de ponto flutuante. Se uma enumeração for atribuída a um valor de ponto flutuante com `Option Strict On`, ocorrerá um erro de compilador. Se `Option Strict` for `Off`, o valor será convertido automaticamente no tipo de `Enum`.  
  
 Para obter informações sobre nomes e como usar a instrução `Imports` para tornar a qualificação de nome desnecessária, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Para declarar uma enumeração  
  
1. Escreva uma declaração que inclua um nível de acesso de código, a palavra-chave `Enum` e um nome válido, como nos exemplos a seguir, sendo que cada uma declara um `Enum`diferente.  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Defina as constantes na enumeração. Por padrão, a primeira constante em uma enumeração é inicializada para `0`e as constantes subsequentes são inicializadas para um valor mais um que a constante anterior. Por exemplo, a seguinte enumeração, `Days`, contém uma constante chamada `Sunday` com o valor `0`, uma constante chamada `Monday` com o valor `1`, uma constante chamada `Tuesday` com o valor de `2`e assim por diante.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Você pode atribuir explicitamente valores a constantes em uma enumeração usando uma instrução de atribuição. Você pode atribuir qualquer valor inteiro, incluindo números negativos. Por exemplo, você pode querer que constantes com valores menores que zero representem condições de erro. Na enumeração a seguir, a constante `Invalid` é atribuída explicitamente ao valor `–1`e a constante `Sunday` é atribuída ao valor `0`. Como é a primeira constante na enumeração, `Saturday` também é inicializada para o valor `0`. O valor de `Monday` é `1` (um maior que o valor de `Sunday`); o valor de `Tuesday` é `2`e assim por diante.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Para declarar uma enumeração como um tipo explícito  
  
- Especifique o tipo de enumeração usando a cláusula `As`, conforme mostrado no exemplo a seguir.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Como: iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Visão Geral de Constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)

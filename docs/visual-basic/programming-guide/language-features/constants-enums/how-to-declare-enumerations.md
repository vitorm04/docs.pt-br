---
title: 'Como: Declarar enumerações (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: f168d6d9cd6970353e75fa35a7e52cc7156fda72
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343331"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Como: Declarar enumerações (Visual Basic)
Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou módulo. Você não pode declarar uma enumeração dentro de um método. Para especificar o nível apropriado de acesso, use `Private`, `Protected`, `Friend`, ou `Public`.  
  
 Um `Enum` tipo tem um nome, um tipo subjacente e um conjunto de campos, cada um representando uma constante. O nome deve ser um qualificador de Visual Basic .NET válido. O tipo subjacente deve ser um dos tipos inteiros —`Byte`, `Short`, `Long` ou `Integer`. `Integer` é o padrão. Enumerações são sempre fortemente tipadas e não são intercambiáveis com tipos de número inteiro.  
  
 Enumerações não podem ter valores de ponto flutuante. Se uma enumeração é atribuída um valor de ponto flutuante com `Option Strict On`, um erro de compilação acontece. Se `Option Strict` está `Off`, o valor é automaticamente convertido para o `Enum` tipo.  
  
 Para obter informações sobre nomes e como usar o `Imports` instrução para tornar a qualificação de nome desnecessária, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Para declarar uma enumeração  
  
1. Escrever uma declaração que inclui um nível de acesso do código, o `Enum` palavra-chave e um nome válido, como nos exemplos a seguir, cada uma das quais declara um diferentes `Enum`.  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Defina as constantes na enumeração. Por padrão, a primeira constante em uma enumeração é inicializada como `0`, e constantes subsequentes são inicializados com um valor de um mais do que a constante anterior. Por exemplo, a seguinte enumeração `Days`, contém uma constante chamada `Sunday` com o valor `0`, uma constante chamada `Monday` com o valor `1`, uma constante chamada `Tuesday` com o valor de `2`e assim por diante.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Explicitamente, você pode atribuir valores às constantes em uma enumeração usando uma instrução de atribuição. Você pode atribuir qualquer valor inteiro, incluindo os números negativos. Por exemplo, você pode querer constantes com valores menores que zero para representar as condições de erro. Na seguinte enumeração, a constante `Invalid` é o valor explicitamente atribuído `–1`e a constante `Sunday` recebe o valor `0`. Porque é a primeira constante na enumeração, `Saturday` também é inicializada com o valor `0`. O valor de `Monday` está `1` (um a mais do que o valor de `Sunday`); o valor de `Tuesday` é `2`e assim por diante.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Para declarar uma enumeração como um tipo explícito  
  
-   Especifique o tipo de enumeração usando o `As` cláusula, conforme mostrado no exemplo a seguir.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Como: Fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Como: Iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Como: Determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Visão Geral de Constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)

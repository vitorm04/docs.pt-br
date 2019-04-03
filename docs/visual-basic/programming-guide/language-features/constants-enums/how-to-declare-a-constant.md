---
title: 'Como: Declarar uma constante (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 95bfa3da5499c518dad0c235b539784fee2bb522
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843403"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Como: Declarar uma constante (Visual Basic)
Você usa o `Const` instrução para declarar uma constante e defina seu valor. Ao declarar uma constante, você pode atribuir um nome significativo para um valor. Depois que uma constante é declarada, não pode ser modificado ou receber um novo valor.  
  
 Você declarar uma constante dentro de um procedimento ou na seção de declarações de um módulo, classe ou estrutura. Classe ou constantes de nível de estrutura são `Private` por padrão, mas também podem ser declarados como `Public`, `Friend`, `Protected`, ou `Protected Friend` para o nível apropriado de acesso ao código.  
  
 A constante deve ter um nome simbólico válido (as regras são os mesmos para a criação de nomes de variável) e uma expressão composta de numérico ou cadeia de caracteres constantes e operadores (mas nenhuma chamada de função).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Para declarar uma constante  
  
-   Escrever uma declaração que inclui um especificador de acesso, o `Const` palavra-chave e uma expressão, como nos exemplos a seguir:  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar uma constante explicitamente especificando um tipo de dados (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, ou `String`).  
  
     Quando `Option Infer` está `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula. O compilador determina o tipo da constante do tipo da expressão. Para obter mais informações, consulte [constante e Literal tipos de dados](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Para declarar uma constante que tem um tipo de dados explicitamente declarados  
  
-   Escrever uma declaração que inclui o `As` palavra-chave e uma data explícita de tipo, como nos exemplos a seguir:  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     Você pode declarar constantes múltiplas em uma única linha, embora seu código é mais legível, se você declarar uma única constante por linha. Se você declarar constantes múltiplas em uma única linha, elas devem ter o mesmo nível de acesso (`Public`, `Private`, `Friend`, `Protected`, ou `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Para declarar constantes múltiplas em uma única linha  
  
-   Separe as declarações com uma vírgula e um espaço, como no exemplo a seguir:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Tipos de Dados Constante e Literal](constant-and-literal-data-types.md)
- [Visão Geral de Constantes](constants-overview.md)
- [Como: Declarar uma constante](how-to-declare-a-constant.md)
- [Constantes Definidas pelo Usuário](user-defined-constants.md)
- [Tipos de Dados Constante e Literal](constant-and-literal-data-types.md)
- [Como: Agrupar valores constantes relacionados](how-to-group-related-constant-values-together.md)
- [Visão geral de Enumerações](enumerations-overview.md)
- [Como: Declarar enumerações](how-to-declare-enumerations.md)
- [Como: Fazer referência a um membro de enumeração](how-to-refer-to-an-enumeration-member.md)
- [Enumerações e Qualificação de Nome](enumerations-and-name-qualification.md)
- [Como: Iterar por meio de uma enumeração](how-to-iterate-through-an-enumeration.md)
- [Como: Determinar a cadeia de caracteres associada a um valor de enumeração](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quando Usar uma Enumeração](when-to-use-an-enumeration.md)

- [Visão geral de Enumerações](enumerations-overview.md)
- [Visão Geral de Constantes](constants-overview.md)
- [Como: Declarar uma enumeração](how-to-declare-enumerations.md)
- [Enumerações e Qualificação de Nome](enumerations-and-name-qualification.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)

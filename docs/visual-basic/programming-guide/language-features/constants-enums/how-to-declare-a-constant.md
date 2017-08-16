---
title: 'Como: declarar uma constante (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.constant
dev_langs:
- VB
helpviewer_keywords:
- Integer data type, declaring constants
- Single data type, declaring constants
- Const statement [Visual Basic], declaring constants
- procedures, declaration
- data types [Visual Basic], constants
- Long data type, declaring constants
- Visual Basic code, declaring variables and constants
- Double data type, declaring constants
- Boolean data type, declaring constants
- modules, declaring constants
- Byte data type, declaring constants
- constants, declaring
- Date data type, declaring constants
- String data type, declaring constants
- declaring constants, const keyword
- Currency data type, declaring constants and variants
- module-level constants and variables
- Object data type, declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 401d0feb85fccf94a25308d38c3c75198ef9294c
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-a-constant-visual-basic"></a>Como declarar uma constante (Visual Basic)
Você usa o `Const` instrução para declarar uma constante e definir seu valor. Ao declarar uma constante, você atribuir um nome significativo para um valor. Depois que uma constante é declarada, não pode ser modificado ou recebe um novo valor.  
  
 Declarar uma constante dentro de um procedimento ou na seção de declarações de um módulo, classe ou estrutura. Classe ou constantes de nível de estrutura são `Private` por padrão, mas também podem ser declarados como `Public`, `Friend`, `Protected`, ou `Protected Friend` para o nível apropriado de acesso ao código.  
  
 A constante deve ter um nome simbólico válido (as regras são os mesmos para a criação de nomes de variáveis) e uma expressão composta de numérico ou cadeia de caracteres constantes e operadores (mas nenhuma chamada de função).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Para declarar uma constante  
  
-   Escrever uma declaração que inclua um especificador de acesso, o `Const` palavra-chave e uma expressão, como os exemplos a seguir:  
  
     [!code-vb[VbEnumsTask n º&8;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar uma constante explicitamente especificando um tipo de dados (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, ou `String`).  
  
     Quando `Option Infer` é `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula. O compilador determina o tipo da constante do tipo da expressão. Para obter mais informações, consulte [constante e Literal de tipos de dados](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Para declarar uma constante que tem um tipo de dados declarados explicitamente  
  
-   Escreva uma declaração que inclui o `As` digitar palavra-chave e uma data explícita, como os exemplos a seguir:  
  
     [!code-vb[VbEnumsTask n º&9;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     Você pode declarar constantes múltiplas em uma única linha, embora seu código é mais legível se você declarar uma única constante por linha. Se você declarar constantes múltiplas em uma única linha, eles devem todos ter o mesmo nível de acesso (`Public`, `Private`, `Friend`, `Protected`, ou `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Para declarar constantes múltiplas em uma única linha  
  
-   Separe as declarações com uma vírgula e um espaço, como no exemplo a seguir:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Tipos de dados constante e Literal](constant-and-literal-data-types.md)   
 [Visão geral de constantes](constants-overview.md)
 [como: declarar uma constante](how-to-declare-a-constant.md)
 [constantes definidas pelo usuário](user-defined-constants.md)
 [tipos de dados constante e Literal](constant-and-literal-data-types.md)
 [como: agrupar valores constantes relacionados](how-to-group-related-constant-values-together.md)
 [visão geral de enumerações](enumerations-overview.md)
 [como: Declarar enumerações](how-to-declare-enumerations.md)
 [como: referência a um membro de enumeração](how-to-refer-to-an-enumeration-member.md)
 [enumerações e qualificação de nome](enumerations-and-name-qualification.md)
 [como: iterar em uma enumeração](how-to-iterate-through-an-enumeration.md)
 [como: determinar a cadeia de caracteres Associado com um valor de enumeração](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [quando usar uma enumeração](when-to-use-an-enumeration.md)

 [Visão geral de enumerações](enumerations-overview.md)   
 [Visão geral de constantes](constants-overview.md)   
 [Como: declarar uma enumeração](how-to-declare-enumerations.md)   
 [Enumerações e qualificação de nome](enumerations-and-name-qualification.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)


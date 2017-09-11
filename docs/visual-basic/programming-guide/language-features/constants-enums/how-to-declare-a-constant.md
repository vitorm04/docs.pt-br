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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: b7fc499336c2b5db3b4d2fe9c0cd11799ea0ad77
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="3ef11-102">Como declarar uma constante (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ef11-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="3ef11-103">Você usa o `Const` instrução para declarar uma constante e definir seu valor.</span><span class="sxs-lookup"><span data-stu-id="3ef11-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="3ef11-104">Ao declarar uma constante, você atribuir um nome significativo para um valor.</span><span class="sxs-lookup"><span data-stu-id="3ef11-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="3ef11-105">Depois que uma constante é declarada, não pode ser modificado ou recebe um novo valor.</span><span class="sxs-lookup"><span data-stu-id="3ef11-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="3ef11-106">Declarar uma constante dentro de um procedimento ou na seção de declarações de um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="3ef11-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="3ef11-107">Classe ou constantes de nível de estrutura são `Private` por padrão, mas também podem ser declarados como `Public`, `Friend`, `Protected`, ou `Protected Friend` para o nível apropriado de acesso ao código.</span><span class="sxs-lookup"><span data-stu-id="3ef11-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="3ef11-108">A constante deve ter um nome simbólico válido (as regras são os mesmos para a criação de nomes de variáveis) e uma expressão composta de numérico ou cadeia de caracteres constantes e operadores (mas nenhuma chamada de função).</span><span class="sxs-lookup"><span data-stu-id="3ef11-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="3ef11-109">Para declarar uma constante</span><span class="sxs-lookup"><span data-stu-id="3ef11-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="3ef11-110">Escrever uma declaração que inclua um especificador de acesso, o `Const` palavra-chave e uma expressão, como os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ef11-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     <span data-ttu-id="3ef11-111">[!code-vb[VbEnumsTask n º&8;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3ef11-111">[!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]</span></span>  
  
     <span data-ttu-id="3ef11-112">Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar uma constante explicitamente especificando um tipo de dados (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, ou `String`).</span><span class="sxs-lookup"><span data-stu-id="3ef11-112">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="3ef11-113">Quando `Option Infer` é `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="3ef11-113">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="3ef11-114">O compilador determina o tipo da constante do tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="3ef11-114">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="3ef11-115">Para obter mais informações, consulte [constante e Literal de tipos de dados](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="3ef11-115">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="3ef11-116">Para declarar uma constante que tem um tipo de dados declarados explicitamente</span><span class="sxs-lookup"><span data-stu-id="3ef11-116">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="3ef11-117">Escreva uma declaração que inclui o `As` digitar palavra-chave e uma data explícita, como os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ef11-117">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     <span data-ttu-id="3ef11-118">[!code-vb[VbEnumsTask n º&9;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="3ef11-118">[!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]</span></span>  
  
     <span data-ttu-id="3ef11-119">Você pode declarar constantes múltiplas em uma única linha, embora seu código é mais legível se você declarar uma única constante por linha.</span><span class="sxs-lookup"><span data-stu-id="3ef11-119">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="3ef11-120">Se você declarar constantes múltiplas em uma única linha, eles devem todos ter o mesmo nível de acesso (`Public`, `Private`, `Friend`, `Protected`, ou `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="3ef11-120">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="3ef11-121">Para declarar constantes múltiplas em uma única linha</span><span class="sxs-lookup"><span data-stu-id="3ef11-121">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="3ef11-122">Separe as declarações com uma vírgula e um espaço, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ef11-122">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3ef11-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ef11-123">See Also</span></span>  
 <span data-ttu-id="3ef11-124">[Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3ef11-124">[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="3ef11-125"> [Tipos de dados constante e Literal](constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="3ef11-125"> [Constant and Literal Data Types](constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="3ef11-126"> [Visão geral de constantes](constants-overview.md)
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
 [quando usar uma enumeração](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="3ef11-126"> [Constants Overview](constants-overview.md)
 [How to: Declare A Constant](how-to-declare-a-constant.md)
 [User-Defined Constants](user-defined-constants.md)
 [Constant and Literal Data Types](constant-and-literal-data-types.md)
 [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md)
 [Enumerations Overview](enumerations-overview.md)
 [How to: Declare Enumerations](how-to-declare-enumerations.md)
 [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md)
 [Enumerations and Name Qualification](enumerations-and-name-qualification.md)
 [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md)
 [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 <span data-ttu-id="3ef11-127">[Visão geral de enumerações](enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="3ef11-127">[Enumerations Overview](enumerations-overview.md) </span></span>  
<span data-ttu-id="3ef11-128"> [Visão geral de constantes](constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="3ef11-128"> [Constants Overview](constants-overview.md) </span></span>  
<span data-ttu-id="3ef11-129"> [Como: declarar uma enumeração](how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="3ef11-129"> [How to: Declare an Enumeration](how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="3ef11-130"> [Enumerações e qualificação de nome](enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="3ef11-130"> [Enumerations and Name Qualification](enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="3ef11-131"> [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3ef11-131"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="3ef11-132"> [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="3ef11-132"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>


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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61975969"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="db008-102">Como: Declarar uma constante (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db008-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="db008-103">Você usa o `Const` instrução para declarar uma constante e defina seu valor.</span><span class="sxs-lookup"><span data-stu-id="db008-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="db008-104">Ao declarar uma constante, você pode atribuir um nome significativo para um valor.</span><span class="sxs-lookup"><span data-stu-id="db008-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="db008-105">Depois que uma constante é declarada, não pode ser modificado ou receber um novo valor.</span><span class="sxs-lookup"><span data-stu-id="db008-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="db008-106">Você declarar uma constante dentro de um procedimento ou na seção de declarações de um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="db008-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="db008-107">Classe ou constantes de nível de estrutura são `Private` por padrão, mas também podem ser declarados como `Public`, `Friend`, `Protected`, ou `Protected Friend` para o nível apropriado de acesso ao código.</span><span class="sxs-lookup"><span data-stu-id="db008-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="db008-108">A constante deve ter um nome simbólico válido (as regras são os mesmos para a criação de nomes de variável) e uma expressão composta de numérico ou cadeia de caracteres constantes e operadores (mas nenhuma chamada de função).</span><span class="sxs-lookup"><span data-stu-id="db008-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="db008-109">Para declarar uma constante</span><span class="sxs-lookup"><span data-stu-id="db008-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="db008-110">Escrever uma declaração que inclui um especificador de acesso, o `Const` palavra-chave e uma expressão, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="db008-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="db008-111">Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar uma constante explicitamente especificando um tipo de dados (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, ou `String`).</span><span class="sxs-lookup"><span data-stu-id="db008-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="db008-112">Quando `Option Infer` está `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="db008-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="db008-113">O compilador determina o tipo da constante do tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="db008-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="db008-114">Para obter mais informações, consulte [constante e Literal tipos de dados](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="db008-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="db008-115">Para declarar uma constante que tem um tipo de dados explicitamente declarados</span><span class="sxs-lookup"><span data-stu-id="db008-115">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="db008-116">Escrever uma declaração que inclui o `As` palavra-chave e uma data explícita de tipo, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="db008-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="db008-117">Você pode declarar constantes múltiplas em uma única linha, embora seu código é mais legível, se você declarar uma única constante por linha.</span><span class="sxs-lookup"><span data-stu-id="db008-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="db008-118">Se você declarar constantes múltiplas em uma única linha, elas devem ter o mesmo nível de acesso (`Public`, `Private`, `Friend`, `Protected`, ou `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="db008-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="db008-119">Para declarar constantes múltiplas em uma única linha</span><span class="sxs-lookup"><span data-stu-id="db008-119">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="db008-120">Separe as declarações com uma vírgula e um espaço, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="db008-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="db008-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db008-121">See also</span></span>

- [<span data-ttu-id="db008-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="db008-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="db008-123">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="db008-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="db008-124">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="db008-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="db008-125">Como: Declarar uma constante</span><span class="sxs-lookup"><span data-stu-id="db008-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="db008-126">Constantes Definidas pelo Usuário</span><span class="sxs-lookup"><span data-stu-id="db008-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="db008-127">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="db008-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="db008-128">Como: Agrupar valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="db008-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="db008-129">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="db008-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="db008-130">Como: Declarar enumerações</span><span class="sxs-lookup"><span data-stu-id="db008-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="db008-131">Como: Fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="db008-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="db008-132">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="db008-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="db008-133">Como: Iterar por meio de uma enumeração</span><span class="sxs-lookup"><span data-stu-id="db008-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="db008-134">Como: Determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="db008-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="db008-135">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="db008-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="db008-136">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="db008-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="db008-137">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="db008-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="db008-138">Como: Declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="db008-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="db008-139">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="db008-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="db008-140">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="db008-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="db008-141">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="db008-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)

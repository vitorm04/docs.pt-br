---
title: Como declarar uma constante
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
ms.openlocfilehash: ffaa98f6af3d4b276f5c0b1153841acdea0809d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414473"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="a02c2-102">Como declarar uma constante (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a02c2-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="a02c2-103">Você usa a `Const` instrução para declarar uma constante e definir seu valor.</span><span class="sxs-lookup"><span data-stu-id="a02c2-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="a02c2-104">Ao declarar uma constante, você atribui um nome significativo a um valor.</span><span class="sxs-lookup"><span data-stu-id="a02c2-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="a02c2-105">Depois que uma constante é declarada, ela não pode ser modificada ou atribuída um novo valor.</span><span class="sxs-lookup"><span data-stu-id="a02c2-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="a02c2-106">Você declara uma constante em um procedimento ou na seção declarações de um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a02c2-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="a02c2-107">As constantes de nível de classe ou estrutura são `Private` por padrão, mas também podem ser declaradas como `Public` , `Friend` , `Protected` ou `Protected Friend` para o nível apropriado de acesso ao código.</span><span class="sxs-lookup"><span data-stu-id="a02c2-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="a02c2-108">A constante deve ter um nome simbólico válido (as regras são as mesmas que as para criar nomes de variáveis) e uma expressão composta por constantes numéricas ou de cadeia de caracteres e operadores (mas sem chamadas de função).</span><span class="sxs-lookup"><span data-stu-id="a02c2-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="a02c2-109">Para declarar uma constante</span><span class="sxs-lookup"><span data-stu-id="a02c2-109">To declare a constant</span></span>  
  
- <span data-ttu-id="a02c2-110">Escreva uma declaração que inclua um especificador de acesso, a `Const` palavra-chave e uma expressão, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="a02c2-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="a02c2-111">Quando [Option Infer](../../../language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../language-reference/statements/option-strict-statement.md) é `On` , você deve declarar uma constante explicitamente especificando um tipo de dados (,,,, `Boolean` `Byte` `Char` `DateTime` `Decimal` , `Double` , `Integer` , `Long` , `Short` , `Single` ou `String` ).</span><span class="sxs-lookup"><span data-stu-id="a02c2-111">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="a02c2-112">Quando `Option Infer` é `On` ou `Option Strict` é `Off` , você pode declarar uma constante sem especificar um tipo de dados com uma `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="a02c2-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="a02c2-113">O compilador determina o tipo da constante do tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="a02c2-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="a02c2-114">Para obter mais informações, consulte [constantes e tipos de dados literais](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a02c2-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="a02c2-115">Para declarar uma constante que tem um tipo de dados explicitamente declarado</span><span class="sxs-lookup"><span data-stu-id="a02c2-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="a02c2-116">Escreva uma declaração que inclua a `As` palavra-chave e um tipo de dados explícito, como nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="a02c2-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="a02c2-117">Você pode declarar várias constantes em uma única linha, embora seu código seja mais legível se você declarar apenas uma única constante por linha.</span><span class="sxs-lookup"><span data-stu-id="a02c2-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="a02c2-118">Se você declarar várias constantes em uma única linha, todas elas deverão ter o mesmo nível de acesso ( `Public` , `Private` ,, `Friend` `Protected` ou `Protected Friend` ).</span><span class="sxs-lookup"><span data-stu-id="a02c2-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="a02c2-119">Para declarar várias constantes em uma única linha</span><span class="sxs-lookup"><span data-stu-id="a02c2-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="a02c2-120">Separe as declarações com uma vírgula e um espaço, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a02c2-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a02c2-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="a02c2-121">See also</span></span>

- [<span data-ttu-id="a02c2-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="a02c2-122">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="a02c2-123">Tipos de dados constante e literal</span><span class="sxs-lookup"><span data-stu-id="a02c2-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="a02c2-124">Visão geral de constantes</span><span class="sxs-lookup"><span data-stu-id="a02c2-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="a02c2-125">Como declarar uma constante</span><span class="sxs-lookup"><span data-stu-id="a02c2-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="a02c2-126">Constantes definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="a02c2-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="a02c2-127">Tipos de dados constante e literal</span><span class="sxs-lookup"><span data-stu-id="a02c2-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="a02c2-128">Como agrupar valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="a02c2-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="a02c2-129">Visão geral de enumerações</span><span class="sxs-lookup"><span data-stu-id="a02c2-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="a02c2-130">Como Declarar Enumerações</span><span class="sxs-lookup"><span data-stu-id="a02c2-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="a02c2-131">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="a02c2-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="a02c2-132">Enumerações e qualificação de nome</span><span class="sxs-lookup"><span data-stu-id="a02c2-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="a02c2-133">Como iterar em uma enumeração</span><span class="sxs-lookup"><span data-stu-id="a02c2-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="a02c2-134">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="a02c2-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="a02c2-135">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="a02c2-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="a02c2-136">Visão geral de enumerações</span><span class="sxs-lookup"><span data-stu-id="a02c2-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="a02c2-137">Visão geral de constantes</span><span class="sxs-lookup"><span data-stu-id="a02c2-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="a02c2-138">Como declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="a02c2-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="a02c2-139">Enumerações e qualificação de nome</span><span class="sxs-lookup"><span data-stu-id="a02c2-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="a02c2-140">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="a02c2-140">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="a02c2-141">Constantes e enumerações</span><span class="sxs-lookup"><span data-stu-id="a02c2-141">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)

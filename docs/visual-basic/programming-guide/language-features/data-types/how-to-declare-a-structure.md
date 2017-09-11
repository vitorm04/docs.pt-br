---
title: 'Como: declarar uma estrutura (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declarations, structures
- structure statements
- statements [Visual Basic], structure
- structures, declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: 15
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: af1bfeb3eed7d8cc05db23a69576c180be473711
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="1dc20-102">Como declarar uma estrutura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dc20-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="1dc20-103">Começar com uma declaração de estrutura de [instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md), e termina com o `End` `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="1dc20-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End` `Structure` statement.</span></span> <span data-ttu-id="1dc20-104">Entre essas duas instruções, você deve declarar pelo menos um *elemento*.</span><span class="sxs-lookup"><span data-stu-id="1dc20-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="1dc20-105">Os elementos podem ser de qualquer tipo de dados, mas pelo menos um deve ser uma variável não compartilhada ou um evento não compartilhado, não personalizado.</span><span class="sxs-lookup"><span data-stu-id="1dc20-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="1dc20-106">Você não pode inicializar qualquer um dos elementos de estrutura na declaração da estrutura.</span><span class="sxs-lookup"><span data-stu-id="1dc20-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="1dc20-107">Quando você declara uma variável para ser de um tipo de estrutura, atribuir valores para os elementos, acessando-los por meio da variável.</span><span class="sxs-lookup"><span data-stu-id="1dc20-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="1dc20-108">Para uma discussão sobre as diferenças entre as estruturas e classes, consulte [estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="1dc20-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="1dc20-109">Para fins de demonstração, considere uma situação em que você deseja manter o controle de nome, ramal e salário do funcionário.</span><span class="sxs-lookup"><span data-stu-id="1dc20-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="1dc20-110">Uma estrutura permite que você faça isso em uma única variável.</span><span class="sxs-lookup"><span data-stu-id="1dc20-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="1dc20-111">Para declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="1dc20-111">To declare a structure</span></span>  
  
1.  <span data-ttu-id="1dc20-112">Crie o início e final instruções para a estrutura.</span><span class="sxs-lookup"><span data-stu-id="1dc20-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="1dc20-113">Você pode especificar o nível de acesso de uma estrutura usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), ou [particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave, ou você pode permitir que ele padrão `Public`.</span><span class="sxs-lookup"><span data-stu-id="1dc20-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  <span data-ttu-id="1dc20-114">Adicione elementos ao corpo da estrutura.</span><span class="sxs-lookup"><span data-stu-id="1dc20-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="1dc20-115">Uma estrutura deve ter pelo menos um elemento.</span><span class="sxs-lookup"><span data-stu-id="1dc20-115">A structure must have at least one element.</span></span> <span data-ttu-id="1dc20-116">Você deve declarar cada elemento e especificar um nível de acesso para ele.</span><span class="sxs-lookup"><span data-stu-id="1dc20-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="1dc20-117">Se você usar o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sem quaisquer palavras-chave, a acessibilidade padrão é `Public`.</span><span class="sxs-lookup"><span data-stu-id="1dc20-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="1dc20-118">O `salary` campo no exemplo anterior é `Private`, que significa que não está acessível fora da estrutura, até mesmo de classe que contém.</span><span class="sxs-lookup"><span data-stu-id="1dc20-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="1dc20-119">No entanto, o `giveRaise` procedimento é `Public`, portanto, ele pode ser chamado de fora da estrutura.</span><span class="sxs-lookup"><span data-stu-id="1dc20-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="1dc20-120">Da mesma forma, você pode gerar o `salaryReviewTime` evento de fora da estrutura.</span><span class="sxs-lookup"><span data-stu-id="1dc20-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="1dc20-121">Além de variáveis, `Sub` procedimentos e eventos, você também pode definir constantes, `Function` procedimentos e propriedades em uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="1dc20-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="1dc20-122">Você pode designar no máximo uma propriedade como o *propriedade padrão*, desde que ela tem pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="1dc20-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="1dc20-123">Você pode manipular um evento com um [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="1dc20-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="1dc20-124">Para obter mais informações, consulte [como: declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="1dc20-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc20-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dc20-125">See Also</span></span>  
 <span data-ttu-id="1dc20-126">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-126">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="1dc20-127"> [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-127"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="1dc20-128"> [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-128"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="1dc20-129"> [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-129"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="1dc20-130"> [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-130"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="1dc20-131"> [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-131"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="1dc20-132"> [Variáveis de estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-132"> [Structure Variables](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md) </span></span>  
<span data-ttu-id="1dc20-133"> [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-133"> [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span></span>  
<span data-ttu-id="1dc20-134"> [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md) </span><span class="sxs-lookup"><span data-stu-id="1dc20-134"> [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md) </span></span>  
<span data-ttu-id="1dc20-135"> [Tipo de Dados Definido pelo Usuário](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="1dc20-135"> [User-Defined Data Type](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)</span></span>

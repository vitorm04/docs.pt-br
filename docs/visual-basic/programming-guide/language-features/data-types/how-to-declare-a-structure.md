---
title: Como declarar uma estrutura
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 41d2d03064dea703909218de56feb863526c220b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350004"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="19c2b-102">Como declarar uma estrutura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19c2b-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="19c2b-103">Você começa uma declaração de estrutura com a [instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)e a encerra com a instrução `End Structure`.</span><span class="sxs-lookup"><span data-stu-id="19c2b-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="19c2b-104">Entre essas duas instruções, você deve declarar pelo menos um *elemento*.</span><span class="sxs-lookup"><span data-stu-id="19c2b-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="19c2b-105">Os elementos podem ser de qualquer tipo de dados, mas pelo menos um deve ser uma variável não compartilhada ou um evento não compartilhado e não-personalizado.</span><span class="sxs-lookup"><span data-stu-id="19c2b-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="19c2b-106">Você não pode inicializar nenhum dos elementos de estrutura na declaração de estrutura.</span><span class="sxs-lookup"><span data-stu-id="19c2b-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="19c2b-107">Quando você declara uma variável para ser de um tipo de estrutura, você atribui valores aos elementos acessando-os por meio da variável.</span><span class="sxs-lookup"><span data-stu-id="19c2b-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="19c2b-108">Para obter uma discussão sobre as diferenças entre estruturas e classes, consulte [estruturas e classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="19c2b-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="19c2b-109">Para fins de demonstração, considere uma situação em que você deseja acompanhar o nome, a extensão do telefone e o salário de um funcionário.</span><span class="sxs-lookup"><span data-stu-id="19c2b-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="19c2b-110">Uma estrutura permite que você faça isso em uma única variável.</span><span class="sxs-lookup"><span data-stu-id="19c2b-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="19c2b-111">Para declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="19c2b-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="19c2b-112">Crie as instruções inicial e final para a estrutura.</span><span class="sxs-lookup"><span data-stu-id="19c2b-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="19c2b-113">Você pode especificar o nível de acesso de uma estrutura usando a palavra-chave [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)ou [Private](../../../../visual-basic/language-reference/modifiers/private.md) , ou pode deixar que ela seja padronizada para `Public`.</span><span class="sxs-lookup"><span data-stu-id="19c2b-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="19c2b-114">Adicione elementos ao corpo da estrutura.</span><span class="sxs-lookup"><span data-stu-id="19c2b-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="19c2b-115">Uma estrutura deve ter pelo menos um elemento.</span><span class="sxs-lookup"><span data-stu-id="19c2b-115">A structure must have at least one element.</span></span> <span data-ttu-id="19c2b-116">Você deve declarar todos os elementos e especificar um nível de acesso para ele.</span><span class="sxs-lookup"><span data-stu-id="19c2b-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="19c2b-117">Se você usar a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sem nenhuma palavra-chave, o padrão de acessibilidade será `Public`.</span><span class="sxs-lookup"><span data-stu-id="19c2b-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
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
  
     <span data-ttu-id="19c2b-118">O campo `salary` no exemplo anterior é `Private`, o que significa que ele está inacessível fora da estrutura, mesmo da classe que a contém.</span><span class="sxs-lookup"><span data-stu-id="19c2b-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="19c2b-119">No entanto, o procedimento de `giveRaise` é `Public`, portanto, ele pode ser chamado de fora da estrutura.</span><span class="sxs-lookup"><span data-stu-id="19c2b-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="19c2b-120">Da mesma forma, você pode gerar o evento `salaryReviewTime` de fora da estrutura.</span><span class="sxs-lookup"><span data-stu-id="19c2b-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="19c2b-121">Além de variáveis, procedimentos de `Sub` e eventos, você também pode definir constantes, `Function` procedimentos e propriedades em uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="19c2b-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="19c2b-122">Você pode designar, no máximo, uma propriedade como a *propriedade padrão*, desde que ela aceite pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="19c2b-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="19c2b-123">Você pode manipular um evento com um procedimento de`Sub` [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) .</span><span class="sxs-lookup"><span data-stu-id="19c2b-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="19c2b-124">Para obter mais informações, consulte [como: declarar e chamar uma propriedade padrão em Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="19c2b-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c2b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19c2b-125">See also</span></span>

- [<span data-ttu-id="19c2b-126">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="19c2b-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="19c2b-127">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="19c2b-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="19c2b-128">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="19c2b-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="19c2b-129">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="19c2b-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="19c2b-130">Estruturas</span><span class="sxs-lookup"><span data-stu-id="19c2b-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="19c2b-131">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="19c2b-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="19c2b-132">Variáveis de Estrutura</span><span class="sxs-lookup"><span data-stu-id="19c2b-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="19c2b-133">Estruturas e Outros Elementos de Programação</span><span class="sxs-lookup"><span data-stu-id="19c2b-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="19c2b-134">Estruturas e Classes</span><span class="sxs-lookup"><span data-stu-id="19c2b-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="19c2b-135">Tipo de Dados Definido pelo Usuário</span><span class="sxs-lookup"><span data-stu-id="19c2b-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)

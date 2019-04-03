---
title: 'Como: Declarar uma estrutura (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 7fc4aed4d405729b64a2f7ba772cdd794df40f2a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825085"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="67305-102">Como: Declarar uma estrutura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67305-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="67305-103">Começar uma declaração de estrutura com o [instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md), e você encerrá-lo com o `End Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="67305-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="67305-104">Entre essas duas instruções, você deve declarar pelo menos um *elemento*.</span><span class="sxs-lookup"><span data-stu-id="67305-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="67305-105">Os elementos podem ser de qualquer tipo de dados, mas pelo menos um deve ser uma variável não compartilhada ou um evento não compartilhado, não personalizado.</span><span class="sxs-lookup"><span data-stu-id="67305-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="67305-106">Não é possível inicializar todos os elementos de estrutura na declaração de estrutura.</span><span class="sxs-lookup"><span data-stu-id="67305-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="67305-107">Quando você declara uma variável para ser de um tipo de estrutura, atribuir valores aos elementos, acessando-os por meio da variável.</span><span class="sxs-lookup"><span data-stu-id="67305-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="67305-108">Para uma discussão sobre as diferenças entre as estruturas e classes, consulte [estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="67305-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="67305-109">Para fins de demonstração, considere uma situação em que você deseja manter o controle de nome, extensão de telefone e salário do funcionário.</span><span class="sxs-lookup"><span data-stu-id="67305-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="67305-110">Uma estrutura permite que você faça isso em uma única variável.</span><span class="sxs-lookup"><span data-stu-id="67305-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="67305-111">Para declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="67305-111">To declare a structure</span></span>  
  
1.  <span data-ttu-id="67305-112">Crie o início e fim instruções para a estrutura.</span><span class="sxs-lookup"><span data-stu-id="67305-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="67305-113">Você pode especificar o nível de acesso de uma estrutura usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave, ou você pode permitir que ele o padrão `Public`.</span><span class="sxs-lookup"><span data-stu-id="67305-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  <span data-ttu-id="67305-114">Adicione elementos ao corpo da estrutura.</span><span class="sxs-lookup"><span data-stu-id="67305-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="67305-115">Uma estrutura deve ter pelo menos um elemento.</span><span class="sxs-lookup"><span data-stu-id="67305-115">A structure must have at least one element.</span></span> <span data-ttu-id="67305-116">Você deve declarar cada elemento e especificar um nível de acesso para ele.</span><span class="sxs-lookup"><span data-stu-id="67305-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="67305-117">Se você usar o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sem quaisquer palavras-chave, a acessibilidade padrão é `Public`.</span><span class="sxs-lookup"><span data-stu-id="67305-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
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
  
     <span data-ttu-id="67305-118">O `salary` campo no exemplo anterior é `Private`, que significa que ele está inacessível fora da estrutura, até mesmo de classe que o contém.</span><span class="sxs-lookup"><span data-stu-id="67305-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="67305-119">No entanto, o `giveRaise` procedimento é `Public`, de modo que ele possa ser chamado de fora da estrutura.</span><span class="sxs-lookup"><span data-stu-id="67305-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="67305-120">Da mesma forma, você pode gerar o `salaryReviewTime` eventos de fora da estrutura.</span><span class="sxs-lookup"><span data-stu-id="67305-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="67305-121">Além das variáveis, `Sub` procedimentos e eventos, você também pode definir constantes, `Function` procedimentos e propriedades em uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="67305-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="67305-122">Você pode designar no máximo uma propriedade como o *propriedade padrão*, desde que ela tem pelo menos um argumento.</span><span class="sxs-lookup"><span data-stu-id="67305-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="67305-123">Você pode manipular um evento com um [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="67305-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="67305-124">Para obter mais informações, confira [Como: Declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="67305-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67305-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67305-125">See also</span></span>

- [<span data-ttu-id="67305-126">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="67305-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="67305-127">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="67305-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="67305-128">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="67305-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="67305-129">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="67305-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="67305-130">Estruturas</span><span class="sxs-lookup"><span data-stu-id="67305-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="67305-131">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="67305-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="67305-132">Variáveis de Estrutura</span><span class="sxs-lookup"><span data-stu-id="67305-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="67305-133">Estruturas e Outros Elementos de Programação</span><span class="sxs-lookup"><span data-stu-id="67305-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="67305-134">Estruturas e Classes</span><span class="sxs-lookup"><span data-stu-id="67305-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="67305-135">Tipo de Dados Definido pelo Usuário</span><span class="sxs-lookup"><span data-stu-id="67305-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)

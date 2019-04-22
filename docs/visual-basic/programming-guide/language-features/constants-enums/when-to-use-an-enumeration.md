---
title: Quando usar uma enumeração (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825089"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="c39d8-102">Quando usar uma enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c39d8-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="c39d8-103">Enumerações oferecem uma maneira fácil de trabalhar com conjuntos de constantes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="c39d8-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="c39d8-104">Uma enumeração, ou `Enum`, é um nome simbólico para um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="c39d8-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="c39d8-105">Enumerações são tratadas como tipos de dados, e você pode usá-los para criar conjuntos de constantes para uso com variáveis e propriedades.</span><span class="sxs-lookup"><span data-stu-id="c39d8-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="c39d8-106">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="c39d8-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="c39d8-107">Sempre que um procedimento aceita um conjunto limitado de variáveis, considere o uso de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="c39d8-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="c39d8-108">Enumerações Certifique-se para o código mais claro e mais legível, especialmente quando os nomes significativos são usados.</span><span class="sxs-lookup"><span data-stu-id="c39d8-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="c39d8-109">Os benefícios de usar enumerações incluem:</span><span class="sxs-lookup"><span data-stu-id="c39d8-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="c39d8-110">Reduz erros causados por Transpor ou números de erros de digitação.</span><span class="sxs-lookup"><span data-stu-id="c39d8-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="c39d8-111">Torna mais fácil alterar os valores no futuro.</span><span class="sxs-lookup"><span data-stu-id="c39d8-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="c39d8-112">Torna o código mais fácil de ler, que significa que é menos provável que os erros serão surgir nele.</span><span class="sxs-lookup"><span data-stu-id="c39d8-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="c39d8-113">Garante a compatibilidade com versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="c39d8-113">Ensures forward compatibility.</span></span> <span data-ttu-id="c39d8-114">Com enumerações, seu código tem menos probabilidade de falhar se futuramente alguém altera os valores correspondentes aos nomes de membros.</span><span class="sxs-lookup"><span data-stu-id="c39d8-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="c39d8-115">Enumerações de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="c39d8-115">Naming Enumerations</span></span>  
 <span data-ttu-id="c39d8-116">Use uma convenção de nomenclatura para os membros de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c39d8-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="c39d8-117">Quando o Visual Basic encontra um nome de membro de enumeração, uma exceção pode ser lançada se outras bibliotecas de tipo referenciado contêm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="c39d8-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="c39d8-118">Use um prefixo exclusivo que identifica os valores do seu aplicativo ou componente.</span><span class="sxs-lookup"><span data-stu-id="c39d8-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="c39d8-119">Ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome de enumeração ou então, use o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="c39d8-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="c39d8-120">Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="c39d8-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="c39d8-121">Enumerações predefinidas</span><span class="sxs-lookup"><span data-stu-id="c39d8-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="c39d8-122">Visual Basic fornece um número de enumerações predefinidos, como `FirstDayOfWeek` e `MsgBoxResult`, para facilitar o seu código.</span><span class="sxs-lookup"><span data-stu-id="c39d8-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="c39d8-123">Para obter uma lista delas, consulte [constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="c39d8-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39d8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c39d8-124">See also</span></span>

- [<span data-ttu-id="c39d8-125">Como: Declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="c39d8-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="c39d8-126">Como: Fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="c39d8-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="c39d8-127">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="c39d8-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="c39d8-128">Como: Iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c39d8-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="c39d8-129">Como: Determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="c39d8-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="c39d8-130">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="c39d8-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="c39d8-131">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="c39d8-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)

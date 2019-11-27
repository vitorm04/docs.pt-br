---
title: Quando usar uma enumeração
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 5daae8d487ddfe079a54e305e59e32e8ded8f65e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353953"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="e698a-102">Quando usar uma enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e698a-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="e698a-103">As enumerações oferecem uma maneira fácil de trabalhar com conjuntos de constantes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="e698a-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="e698a-104">Uma enumeração, ou `Enum`, é um nome simbólico para um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="e698a-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="e698a-105">As enumerações são tratadas como tipos de dados e você pode usá-las para criar conjuntos de constantes para uso com variáveis e propriedades.</span><span class="sxs-lookup"><span data-stu-id="e698a-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="e698a-106">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="e698a-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="e698a-107">Sempre que um procedimento aceita um conjunto limitado de variáveis, considere o uso de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="e698a-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="e698a-108">As enumerações tornam-se um código mais claro e legível, especialmente quando são usados nomes significativos.</span><span class="sxs-lookup"><span data-stu-id="e698a-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="e698a-109">Os benefícios do uso de enumerações incluem:</span><span class="sxs-lookup"><span data-stu-id="e698a-109">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="e698a-110">Reduz os erros causados pela transposição ou números incorretas de digitação.</span><span class="sxs-lookup"><span data-stu-id="e698a-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="e698a-111">Torna mais fácil alterar valores no futuro.</span><span class="sxs-lookup"><span data-stu-id="e698a-111">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="e698a-112">Torna o código mais fácil de ler, o que significa que é menos provável que os erros possam surgir nele.</span><span class="sxs-lookup"><span data-stu-id="e698a-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="e698a-113">Garante a compatibilidade com o futuro.</span><span class="sxs-lookup"><span data-stu-id="e698a-113">Ensures forward compatibility.</span></span> <span data-ttu-id="e698a-114">Com as enumerações, o código é menos provável de falhar se, posteriormente, alguém alterar os valores correspondentes aos nomes dos membros.</span><span class="sxs-lookup"><span data-stu-id="e698a-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="e698a-115">Enumerações de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="e698a-115">Naming Enumerations</span></span>  
 <span data-ttu-id="e698a-116">Use uma Convenção de nomenclatura para membros de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e698a-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="e698a-117">Quando Visual Basic encontrar um nome de membro de enumeração, uma exceção poderá ser gerada se outras bibliotecas de tipos referenciadas contiverem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="e698a-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="e698a-118">Use um prefixo exclusivo que identifique os valores de seu aplicativo ou componente.</span><span class="sxs-lookup"><span data-stu-id="e698a-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="e698a-119">Ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome da enumeração ou, caso contrário, usar a instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="e698a-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="e698a-120">Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="e698a-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="e698a-121">Enumerações predefinidas</span><span class="sxs-lookup"><span data-stu-id="e698a-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="e698a-122">Visual Basic fornece várias enumerações predefinidas, como `FirstDayOfWeek` e `MsgBoxResult`, para facilitar seu código.</span><span class="sxs-lookup"><span data-stu-id="e698a-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="e698a-123">Para obter uma lista desses [, consulte constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="e698a-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e698a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e698a-124">See also</span></span>

- [<span data-ttu-id="e698a-125">Como declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="e698a-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="e698a-126">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="e698a-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="e698a-127">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="e698a-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="e698a-128">Como: iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e698a-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="e698a-129">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="e698a-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="e698a-130">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="e698a-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="e698a-131">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="e698a-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)

---
title: Quando usar uma enumeração (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ab152687f4f9e4ba6bd032ae7c1352f65af715f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="19f57-102">Quando usar uma enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19f57-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="19f57-103">Enumerações oferecem uma maneira fácil de trabalhar com conjuntos de constantes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="19f57-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="19f57-104">Uma enumeração, ou `Enum`, é um nome simbólico para um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="19f57-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="19f57-105">Enumerações são tratadas como tipos de dados, e você pode usá-los para criar conjuntos de constantes para uso com variáveis e propriedades.</span><span class="sxs-lookup"><span data-stu-id="19f57-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="19f57-106">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="19f57-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="19f57-107">Sempre que um procedimento aceita um conjunto limitado de variáveis, considere o uso de uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="19f57-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="19f57-108">Enumerações tornar código mais clara e mais legível, especialmente quando são usados nomes significativos.</span><span class="sxs-lookup"><span data-stu-id="19f57-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="19f57-109">Os benefícios do uso de enumerações incluem:</span><span class="sxs-lookup"><span data-stu-id="19f57-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="19f57-110">Reduz os erros causados por Transpor ou números de erros de digitação.</span><span class="sxs-lookup"><span data-stu-id="19f57-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="19f57-111">É fácil alterar os valores no futuro.</span><span class="sxs-lookup"><span data-stu-id="19f57-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="19f57-112">Torna o código mais fácil de ler, o que significa que é menos provável que os erros serão surgir nele.</span><span class="sxs-lookup"><span data-stu-id="19f57-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="19f57-113">Garante a compatibilidade com versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="19f57-113">Ensures forward compatibility.</span></span> <span data-ttu-id="19f57-114">Com enumerações, seu código tem menos probabilidade de falhar se futuramente alguém altera os valores correspondentes aos nomes de membros.</span><span class="sxs-lookup"><span data-stu-id="19f57-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="19f57-115">Enumerações de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="19f57-115">Naming Enumerations</span></span>  
 <span data-ttu-id="19f57-116">Use uma convenção de nomenclatura para os membros da enumeração.</span><span class="sxs-lookup"><span data-stu-id="19f57-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="19f57-117">Quando o Visual Basic encontre um nome de membro de enumeração, uma exceção pode ser acionada se outras bibliotecas de tipo referenciado com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="19f57-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="19f57-118">Use um prefixo exclusivo que identifica os valores do seu aplicativo ou componente.</span><span class="sxs-lookup"><span data-stu-id="19f57-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="19f57-119">Ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome de enumeração ou então usar o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="19f57-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="19f57-120">Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="19f57-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="19f57-121">Enumerações predefinidas</span><span class="sxs-lookup"><span data-stu-id="19f57-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="19f57-122">Visual Basic oferece um número de enumerações predefinidos, como `FirstDayOfWeek` e `MsgBoxResult`, para facilitar o seu código.</span><span class="sxs-lookup"><span data-stu-id="19f57-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="19f57-123">Para obter uma lista delas, consulte [constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="19f57-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f57-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19f57-124">See Also</span></span>  
 [<span data-ttu-id="19f57-125">Como: declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="19f57-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="19f57-126">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="19f57-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="19f57-127">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="19f57-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="19f57-128">Como: iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19f57-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="19f57-129">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="19f57-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="19f57-130">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="19f57-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="19f57-131">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="19f57-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)

---
title: "Quando usar uma enumeração (Visual Basic) | Documentos do Microsoft"
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
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
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
ms.openlocfilehash: 3853950382fd4336c569f9d772aea3c1312f2ebc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="15247-102">Quando usar uma enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15247-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="15247-103">Enumerações oferecem uma maneira fácil de trabalhar com conjuntos de constantes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="15247-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="15247-104">Uma enumeração, ou `Enum`, é um nome simbólico para um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="15247-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="15247-105">Enumerações são tratadas como tipos de dados, e você pode usá-las para criar conjuntos de constantes para uso com variáveis e propriedades.</span><span class="sxs-lookup"><span data-stu-id="15247-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="15247-106">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="15247-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="15247-107">Sempre que um procedimento aceita um conjunto limitado de variáveis, considere usar uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="15247-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="15247-108">Enumerações fazem para código mais claro e mais legível, especialmente quando são utilizados nomes significativos.</span><span class="sxs-lookup"><span data-stu-id="15247-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="15247-109">Os benefícios de usar enumerações incluem:</span><span class="sxs-lookup"><span data-stu-id="15247-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="15247-110">Reduz erros causados por transpondo ou números de erros de digitação.</span><span class="sxs-lookup"><span data-stu-id="15247-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="15247-111">É fácil alterar os valores no futuro.</span><span class="sxs-lookup"><span data-stu-id="15247-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="15247-112">Torna o código mais fácil de ler, que significa que é menos provável que os erros serão surgir dentro dele.</span><span class="sxs-lookup"><span data-stu-id="15247-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="15247-113">Garante a compatibilidade com versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="15247-113">Ensures forward compatibility.</span></span> <span data-ttu-id="15247-114">Com enumerações, seu código é menor probabilidade de falhar se futuramente alguém altera os valores correspondentes aos nomes de membro.</span><span class="sxs-lookup"><span data-stu-id="15247-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="15247-115">Enumerações de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="15247-115">Naming Enumerations</span></span>  
 <span data-ttu-id="15247-116">Use uma convenção de nomenclatura para membros de enumeração.</span><span class="sxs-lookup"><span data-stu-id="15247-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="15247-117">Quando [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] encontra um nome de membro de enumeração, uma exceção pode ser disparada se outras bibliotecas de tipo referenciado com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="15247-117">When [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="15247-118">Use um prefixo exclusivo que identifica os valores do seu aplicativo ou componente.</span><span class="sxs-lookup"><span data-stu-id="15247-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="15247-119">Ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome da enumeração ou então usar o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="15247-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="15247-120">Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="15247-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="15247-121">Enumerações predefinidas</span><span class="sxs-lookup"><span data-stu-id="15247-121">Predefined Enumerations</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="15247-122">Fornece um número de enumerações predefinidos, como `FirstDayOfWeek` e `MsgBoxResul`t, para facilitar o seu código.</span><span class="sxs-lookup"><span data-stu-id="15247-122"> provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResul`t, to facilitate your code.</span></span> <span data-ttu-id="15247-123">Para obter uma lista desses consulte [constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="15247-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15247-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15247-124">See Also</span></span>  
 <span data-ttu-id="15247-125">[Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="15247-125">[How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="15247-126"> [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="15247-126"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="15247-127"> [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="15247-127"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="15247-128"> [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="15247-128"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="15247-129"> [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="15247-129"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="15247-130"> [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="15247-130"> [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="15247-131"> [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="15247-131"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>

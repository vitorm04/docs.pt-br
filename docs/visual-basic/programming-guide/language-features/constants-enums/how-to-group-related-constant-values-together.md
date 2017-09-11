---
title: 'Como: agrupar valores constantes relacionados (Visual Basic) | Documentos do Microsoft'
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
- enumerations [Visual Basic], constants
- constants, grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: 17
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
ms.openlocfilehash: 6db0b94057406b287b4664a3777a0e1db7f104d4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="e7154-102">Como agrupar valores constantes relacionados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7154-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="e7154-103">Uma enumeração é a melhor maneira de agrupar constantes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="e7154-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="e7154-104">Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="e7154-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="e7154-105">Para obter mais informações, consulte [como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="e7154-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="e7154-106">Para o grupo de valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="e7154-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="e7154-107">Escrever uma declaração que inclua um nível de acesso de código, o `Enum` palavra-chave e um nome válido.</span><span class="sxs-lookup"><span data-stu-id="e7154-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="e7154-108">Este exemplo cria o `Private` enumeração, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="e7154-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     <span data-ttu-id="e7154-109">[!code-vb[VbEnumsTask&#21;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7154-109">[!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]</span></span>  
  
2.  <span data-ttu-id="e7154-110">Defina as constantes na enumeração.</span><span class="sxs-lookup"><span data-stu-id="e7154-110">Define the constants in the enumeration.</span></span> <span data-ttu-id="e7154-111">Este exemplo cria o `Public` enumeração `temperatureValues` e atribui seus valores.</span><span class="sxs-lookup"><span data-stu-id="e7154-111">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     <span data-ttu-id="e7154-112">[!code-vb[VbEnumsTask n º&1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7154-112">[!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7154-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7154-113">See Also</span></span>  
 <span data-ttu-id="e7154-114">[Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-114">[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="e7154-115"> [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-115"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="e7154-116"> [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-116"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span></span>  
<span data-ttu-id="e7154-117"> [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-117"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="e7154-118"> [Tipos de dados constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-118"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="e7154-119"> [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="e7154-119"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>

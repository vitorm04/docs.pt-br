---
title: "Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32124
- bc32124
dev_langs:
- VB
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: 8
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
ms.openlocfilehash: 2ec73306329351ff2594b2e089f8ae0bcc539e9e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="86911-102">Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita</span><span class="sxs-lookup"><span data-stu-id="86911-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="86911-103">Um procedimento é declarado com um parâmetro opcional que usa um parâmetro de tipo que não está restrito a ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="86911-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="86911-104">Você sempre deve fornecer um valor padrão para cada parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="86911-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="86911-105">Se o parâmetro é de um tipo de referência, o valor opcional deve ser `Nothing`, que é um valor válido para qualquer tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="86911-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="86911-106">No entanto, se o parâmetro é de um tipo de valor, esse tipo deve ser um tipo de dados elementar predefinido pelo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86911-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="86911-107">Isso ocorre porque um tipo de valor composto, como uma estrutura definida pelo usuário, tem nenhum valor padrão válido.</span><span class="sxs-lookup"><span data-stu-id="86911-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="86911-108">Quando você usa um parâmetro de tipo para um parâmetro opcional, você deve assegurar-se de um tipo de referência para evitar a possibilidade de um tipo de valor com nenhum valor padrão válido.</span><span class="sxs-lookup"><span data-stu-id="86911-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="86911-109">Isso significa que você deve restringir o parâmetro de tipo com o `Class` palavra-chave ou com o nome de uma classe específica.</span><span class="sxs-lookup"><span data-stu-id="86911-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="86911-110">**ID do erro:** BC32124</span><span class="sxs-lookup"><span data-stu-id="86911-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="86911-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="86911-111">To correct this error</span></span>  
  
-   <span data-ttu-id="86911-112">Restringir o parâmetro de tipo para aceitar apenas um tipo de referência, ou não usá-lo para o parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="86911-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86911-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86911-113">See Also</span></span>  
 <span data-ttu-id="86911-114">[Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="86911-114">[Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="86911-115"> [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md) </span><span class="sxs-lookup"><span data-stu-id="86911-115"> [Type List](../../../visual-basic/language-reference/statements/type-list.md) </span></span>  
<span data-ttu-id="86911-116"> [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) </span><span class="sxs-lookup"><span data-stu-id="86911-116"> [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) </span></span>  
<span data-ttu-id="86911-117"> [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="86911-117"> [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span></span>  
<span data-ttu-id="86911-118"> [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="86911-118"> [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="86911-119"> [Nothing](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="86911-119"> [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>

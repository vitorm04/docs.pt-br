---
title: "Palavras-chave como nomes de elementos em código (Visual Basic) | Documentos do Microsoft"
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
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts
- element names, in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: 11
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
ms.openlocfilehash: 3951d3d918f0fd22b200a2e83ff07a95fd51e378
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="84741-102">Palavras-chave como nomes de elemento em código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84741-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="84741-103">Qualquer elemento de programa — como uma variável, classe ou membro — pode ter o mesmo nome que uma palavra-chave restrita.</span><span class="sxs-lookup"><span data-stu-id="84741-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="84741-104">Por exemplo, você pode criar uma variável chamada `Loop`.</span><span class="sxs-lookup"><span data-stu-id="84741-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="84741-105">No entanto, para se referir a sua versão disso — que tem o mesmo nome restritas `Loop` palavra-chave — você deve precedê-lo com uma cadeia de caracteres de qualificação completa ou colocá-lo entre colchetes (`[ ]`), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="84741-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 <span data-ttu-id="84741-106">[!code-vb[VbVbcnConventions n º&8;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="84741-106">[!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="84741-107">Se você não fizer um deles, Visual Basic assume o uso da intrínseca `Loop` palavra-chave e produz um erro, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="84741-107">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="84741-108">Você pode usar colchetes quando referir a formulários e controles e quando declarando uma variável ou definindo um procedimento com o mesmo nome que uma palavra chave restrita.</span><span class="sxs-lookup"><span data-stu-id="84741-108">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="84741-109">É fácil esquecer de qualificar nomes ou incluir colchetes e, portanto, introduzir erros em seu código e torná-lo mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="84741-109">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="84741-110">Por esse motivo, recomendamos que você não use palavras-chave restritas como nomes de elementos de programa.</span><span class="sxs-lookup"><span data-stu-id="84741-110">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="84741-111">No entanto, se uma versão futura do Visual Basic define uma nova palavra-chave que conflite com um formulário existente ou o nome do controle, em seguida, você pode usar essa técnica quando atualizar seu código para trabalhar com a nova versão.</span><span class="sxs-lookup"><span data-stu-id="84741-111">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84741-112">O programa também pode incluir nomes de elemento fornecidos por outros assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="84741-112">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="84741-113">Se esses nomes entrarem em conflito com palavras-chave restritas, então colocar colchetes em volta deles faz com que o Visual Basic para interpretá-los como seus elementos definidos.</span><span class="sxs-lookup"><span data-stu-id="84741-113">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84741-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84741-114">See Also</span></span>  
 <span data-ttu-id="84741-115">[Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="84741-115">[Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="84741-116"> [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="84741-116"> [Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="84741-117"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)</span><span class="sxs-lookup"><span data-stu-id="84741-117"> [Keywords](../../../visual-basic/language-reference/keywords/index.md)</span></span>

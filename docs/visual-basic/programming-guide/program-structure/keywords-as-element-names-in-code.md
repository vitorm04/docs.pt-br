---
title: "Palavras-chave como nomes de elemento em código (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="a5018-102">Palavras-chave como nomes de elemento em código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5018-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="a5018-103">Qualquer elemento do programa, como uma variável, classe ou membro — pode ter o mesmo nome de uma palavra-chave restrita.</span><span class="sxs-lookup"><span data-stu-id="a5018-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="a5018-104">Por exemplo, você pode criar uma variável chamada `Loop`.</span><span class="sxs-lookup"><span data-stu-id="a5018-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="a5018-105">No entanto, para referir-se à sua versão do mesmo — que tem o mesmo nome que o restrito `Loop` palavra-chave — você deve precedê-lo de uma cadeia de caracteres de qualificação completa ou coloque-o entre colchetes (`[ ]`), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5018-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="a5018-106">Se você não fizer qualquer uma delas, Visual Basic assume o uso de intrínseca `Loop` palavra-chave e produz um erro, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a5018-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="a5018-107">Você pode usar colchetes quando referir a formulários e controles e quando declarando uma variável ou definindo um procedimento com o mesmo nome como uma palavra-chave restrita.</span><span class="sxs-lookup"><span data-stu-id="a5018-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="a5018-108">É fácil esquecer de qualificar nomes ou incluir colchetes e, portanto, introduzir erros em seu código e torná-lo mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="a5018-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="a5018-109">Por esse motivo, é recomendável que você não use palavras-chave restritas como os nomes dos elementos do programa.</span><span class="sxs-lookup"><span data-stu-id="a5018-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="a5018-110">No entanto, se uma versão futura do Visual Basic define uma nova palavra-chave que está em conflito com um formulário existente ou o nome do controle, em seguida, você pode usar essa técnica quando atualizar seu código para trabalhar com a nova versão.</span><span class="sxs-lookup"><span data-stu-id="a5018-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5018-111">O programa também pode incluir nomes de elemento fornecidos por outros assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="a5018-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="a5018-112">Se esses nomes em conflito com palavras-chave restritas, então colocar colchetes ao redor deles faz com que o Visual Basic para interpretá-los como seus elementos definidos.</span><span class="sxs-lookup"><span data-stu-id="a5018-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5018-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5018-113">See Also</span></span>  
 [<span data-ttu-id="a5018-114">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5018-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="a5018-115">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="a5018-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="a5018-116">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a5018-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

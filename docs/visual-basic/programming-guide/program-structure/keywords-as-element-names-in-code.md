---
title: Palavras-chave como nomes de elemento em código (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: c247ada67f6554362f287cf252dd49856c4995da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841141"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="ee0c0-102">Palavras-chave como nomes de elemento em código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee0c0-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="ee0c0-103">Qualquer elemento de programa — como uma variável, classe ou membro — pode ter o mesmo nome que uma palavra-chave restrita.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="ee0c0-104">Por exemplo, você pode criar uma variável chamada `Loop`.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="ee0c0-105">No entanto, para referir-se à sua versão dele — que tem o mesmo nome que restritas `Loop` palavra-chave — você deve precedê-lo com uma cadeia de caracteres de qualificação completa ou coloque-o entre colchetes (`[ ]`), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="ee0c0-106">Se você não fizer uma destas, Visual Basic assume o uso da intrínseca `Loop` palavra-chave e produz um erro, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ee0c0-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="ee0c0-107">Você pode usar colchetes para se referir a formulários e controles e ao declarar uma variável ou definindo um procedimento com o mesmo nome como uma palavra-chave restrita.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="ee0c0-108">É fácil esquecer de qualificar nomes ou incluir colchetes e, portanto, introduzir erros no seu código e torná-lo mais difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="ee0c0-109">Por esse motivo, recomendamos que você não use palavras-chave restritas como os nomes dos elementos do programa.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="ee0c0-110">No entanto, se uma versão futura do Visual Basic define uma nova palavra-chave que está em conflito com um formulário existente ou o nome do controle, em seguida, você pode usar essa técnica quando atualizar seu código para trabalhar com a nova versão.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee0c0-111">O programa também pode incluir nomes de elemento fornecidos por outros assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="ee0c0-112">Se esses nomes em conflito com palavras-chave restritas, então colocar colchetes ao redor deles faz com que o Visual Basic para interpretá-los como seus elementos definidos.</span><span class="sxs-lookup"><span data-stu-id="ee0c0-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee0c0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee0c0-113">See also</span></span>

- [<span data-ttu-id="ee0c0-114">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee0c0-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="ee0c0-115">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="ee0c0-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="ee0c0-116">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ee0c0-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

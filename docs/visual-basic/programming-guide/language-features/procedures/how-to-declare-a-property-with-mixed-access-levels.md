---
title: 'Como: Declarar uma propriedade com níveis de acesso mistos (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: d2b1a80863fe29901554b4912acbbfbdfdab4122
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972575"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="2af02-102">Como: Declarar uma propriedade com níveis de acesso mistos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2af02-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="2af02-103">Se você quiser que o `Get` e `Set` procedimentos de uma propriedade para ter diferentes níveis de acesso, você pode usar o nível mais permissivo na `Property` instrução e o nível mais restritivo em qualquer um os `Get` ou `Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="2af02-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="2af02-104">Você pode usar níveis de acesso mistos em uma propriedade quando você deseja certas partes do código para ser capaz de obter o valor da propriedade e determinadas outras partes do código para ser capaz de alterar o valor.</span><span class="sxs-lookup"><span data-stu-id="2af02-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="2af02-105">Para obter mais informações sobre níveis de acesso, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2af02-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="2af02-106">Para declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="2af02-106">To declare a property with mixed access levels</span></span>  
  
1.  <span data-ttu-id="2af02-107">Declarar a propriedade da maneira normal e especificar o nível de acesso menos restritivo (como `Public`) na `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="2af02-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2.  <span data-ttu-id="2af02-108">Declare a `Get` ou o `Set` procedimento especificando o nível de acesso mais restritivo (como `Friend`).</span><span class="sxs-lookup"><span data-stu-id="2af02-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3.  <span data-ttu-id="2af02-109">Não especifique um nível de acesso em outro procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="2af02-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="2af02-110">Ele pressupõe que o nível de acesso declarado no `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="2af02-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="2af02-111">Você pode restringir o acesso em apenas um dos procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="2af02-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="2af02-112">No exemplo anterior, o `Get` procedimento tem o mesmo `Protected` acesso como a própria propriedade, enquanto o `Set` procedimento tem `Private` acesso.</span><span class="sxs-lookup"><span data-stu-id="2af02-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="2af02-113">Uma classe derivada de `employee` pode ler os `salary` valor, mas apenas o `employee` classe pode defini-lo.</span><span class="sxs-lookup"><span data-stu-id="2af02-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af02-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2af02-114">See also</span></span>
- [<span data-ttu-id="2af02-115">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="2af02-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2af02-116">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="2af02-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2af02-117">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="2af02-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2af02-118">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="2af02-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="2af02-119">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2af02-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="2af02-120">Como: Criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="2af02-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="2af02-121">Como: Chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="2af02-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="2af02-122">Como: Declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2af02-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="2af02-123">Como: Inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="2af02-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="2af02-124">Como: Obter um valor de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="2af02-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)

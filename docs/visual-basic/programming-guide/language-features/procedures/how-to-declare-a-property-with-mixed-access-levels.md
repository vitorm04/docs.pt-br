---
title: Como declarar uma propriedade com níveis de acesso mistos
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
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349691"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="59fb7-102">Como declarar uma propriedade com níveis de acesso mistos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59fb7-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="59fb7-103">Se desejar que os procedimentos `Get` e `Set` em uma propriedade tenham níveis de acesso diferentes, você poderá usar o nível mais permissivo na instrução `Property` e o nível mais restritivo na instrução `Get` ou `Set`.</span><span class="sxs-lookup"><span data-stu-id="59fb7-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="59fb7-104">Você usa níveis de acesso misto em uma propriedade quando você quer que determinadas partes do código possam obter o valor da propriedade e algumas outras partes do código possam alterar o valor.</span><span class="sxs-lookup"><span data-stu-id="59fb7-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="59fb7-105">Para obter mais informações sobre níveis de acesso, consulte [níveis de acesso em Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="59fb7-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="59fb7-106">Para declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="59fb7-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="59fb7-107">Declare a propriedade da maneira normal e especifique o nível de acesso menos restritivo (como `Public`) na instrução `Property`.</span><span class="sxs-lookup"><span data-stu-id="59fb7-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="59fb7-108">Declare o `Get` ou o procedimento `Set` especificando o nível de acesso mais restritivo (como `Friend`).</span><span class="sxs-lookup"><span data-stu-id="59fb7-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="59fb7-109">Não especifique um nível de acesso no outro procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="59fb7-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="59fb7-110">Ele assume o nível de acesso declarado na instrução `Property`.</span><span class="sxs-lookup"><span data-stu-id="59fb7-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="59fb7-111">Você pode restringir o acesso em apenas um dos procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="59fb7-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="59fb7-112">No exemplo anterior, o procedimento `Get` tem o mesmo acesso `Protected` que a própria propriedade, enquanto o procedimento `Set` tem acesso `Private`.</span><span class="sxs-lookup"><span data-stu-id="59fb7-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="59fb7-113">Uma classe derivada de `employee` pode ler o valor de `salary`, mas apenas a classe `employee` pode defini-la.</span><span class="sxs-lookup"><span data-stu-id="59fb7-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59fb7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59fb7-114">See also</span></span>

- [<span data-ttu-id="59fb7-115">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="59fb7-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="59fb7-116">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="59fb7-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="59fb7-117">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="59fb7-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="59fb7-118">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="59fb7-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="59fb7-119">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59fb7-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="59fb7-120">Como criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="59fb7-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="59fb7-121">Como chamar um procedimento de propriedade</span><span class="sxs-lookup"><span data-stu-id="59fb7-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="59fb7-122">Como: declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59fb7-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="59fb7-123">Como inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="59fb7-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- <span data-ttu-id="59fb7-124">Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="59fb7-124">[How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>

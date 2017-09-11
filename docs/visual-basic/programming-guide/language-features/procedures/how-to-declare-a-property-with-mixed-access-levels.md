---
title: "Como: declarar uma propriedade com níveis de acesso mistos (Visual Basic) | Documentos do Microsoft"
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
- access levels, properties
- procedures, defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement, declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: 16
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
ms.openlocfilehash: 096a8e8361c3c25b336588955eb0c58a68dd0c4a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="46400-102">Como declarar uma propriedade com níveis de acesso mistos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46400-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="46400-103">Se você quiser que o `Get` e `Set` procedimentos de uma propriedade ter diferentes níveis de acesso, você pode usar o nível mais permissivo no `Property` instrução e o nível mais restritivo no `Get` ou `Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="46400-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="46400-104">Você pode usar níveis de acesso mistos em uma propriedade certas partes do código para ser capaz de obter o valor da propriedade e determinadas outras partes do código para poder alterar o valor.</span><span class="sxs-lookup"><span data-stu-id="46400-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="46400-105">Para obter mais informações sobre níveis de acesso, consulte [níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46400-105">For more information on access levels, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="46400-106">Para declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="46400-106">To declare a property with mixed access levels</span></span>  
  
1.  <span data-ttu-id="46400-107">Declare a propriedade da forma normal e especificar o nível de acesso menos restritivo (como `Public`) no `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="46400-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2.  <span data-ttu-id="46400-108">Declare o `Get` ou `Set` procedimento especificando o nível de acesso mais restritivo (como `Friend`).</span><span class="sxs-lookup"><span data-stu-id="46400-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3.  <span data-ttu-id="46400-109">Não especifica um nível de acesso em outro procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="46400-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="46400-110">Ele pressupõe que o nível de acesso declarado no `Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="46400-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="46400-111">Você pode restringir o acesso em apenas um dos procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="46400-111">You can restrict access on only one of the property procedures.</span></span>  
  
     <span data-ttu-id="46400-112">[!code-vb[VbVbcnProcedures n º&10;](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="46400-112">[!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]</span></span>  
  
     <span data-ttu-id="46400-113">No exemplo anterior, o `Get` procedimento tem o mesmo `Protected` acesso que a própria propriedade, enquanto o `Set` procedimento tem `Private` acesso.</span><span class="sxs-lookup"><span data-stu-id="46400-113">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="46400-114">Uma classe derivada de `employee` pode ler o `salary` valor, mas apenas o `employee` classe pode defini-lo.</span><span class="sxs-lookup"><span data-stu-id="46400-114">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46400-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46400-115">See Also</span></span>  
 <span data-ttu-id="46400-116">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="46400-116">[Procedures](./index.md) </span></span>  
<span data-ttu-id="46400-117"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="46400-117"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="46400-118"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="46400-118"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="46400-119"> [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="46400-119"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="46400-120"> [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="46400-120"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="46400-121"> [Como: criar uma propriedade](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="46400-121"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="46400-122"> [Como: chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="46400-122"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="46400-123"> [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="46400-123"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="46400-124"> [Como: inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="46400-124"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="46400-125">Como obter um valor de uma propriedade (Visual Basic) [Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="46400-125"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>

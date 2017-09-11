---
title: 'Como: obter um valor de uma propriedade (Visual Basic) | Documentos do Microsoft'
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
- property values
- Visual Basic code, procedures
- values, properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
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
ms.openlocfilehash: 719a4fc9ff163fb4437ea40c8265a5e36232347e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="87477-102">Como obter um valor a partir de uma propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87477-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="87477-103">Para recuperar um valor de propriedade, incluindo o nome da propriedade em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="87477-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="87477-104">A propriedade `Get` procedimento recupera o valor, mas você não chama explicitamente pelo nome.</span><span class="sxs-lookup"><span data-stu-id="87477-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="87477-105">Use a propriedade exatamente como você usaria uma variável.</span><span class="sxs-lookup"><span data-stu-id="87477-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="87477-106">faz as chamadas aos procedimentos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="87477-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="87477-107">Para recuperar um valor de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="87477-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="87477-108">Use o nome da propriedade em uma expressão da mesma maneira que você usaria um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="87477-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="87477-109">Você pode usar uma propriedade em qualquer lugar você pode usar uma variável ou uma constante.</span><span class="sxs-lookup"><span data-stu-id="87477-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="87477-110">-ou-</span><span class="sxs-lookup"><span data-stu-id="87477-110">-or-</span></span>  
  
     <span data-ttu-id="87477-111">Use o nome de propriedade seguido de igual (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="87477-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="87477-112">O exemplo a seguir lê o valor de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `Now` property, implicitamente chamando seu `Get` procedimento.</span><span class="sxs-lookup"><span data-stu-id="87477-112">The following example reads the value of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     <span data-ttu-id="87477-113">[!code-vb[VbVbalrDateProperties n º&4;](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="87477-113">[!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]</span></span>  
  
2.  <span data-ttu-id="87477-114">Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="87477-114">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="87477-115">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="87477-115">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="87477-116">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="87477-116">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="87477-117">Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="87477-117">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="87477-118">O valor da propriedade participa na expressão apenas como uma variável ou constante seria, ou ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="87477-118">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87477-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87477-119">See Also</span></span>  
 <span data-ttu-id="87477-120">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="87477-120">[Procedures](./index.md) </span></span>  
<span data-ttu-id="87477-121"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="87477-121"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="87477-122"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="87477-122"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="87477-123"> [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="87477-123"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="87477-124"> [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="87477-124"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="87477-125"> [Como: criar uma propriedade](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="87477-125"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="87477-126"> [Como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="87477-126"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="87477-127"> [Como: chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="87477-127"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="87477-128"> [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="87477-128"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="87477-129"> [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="87477-129"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md)</span></span>

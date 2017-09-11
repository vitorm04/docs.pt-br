---
title: "Como: definir um parâmetro para um procedimento (Visual Basic) | Documentos do Microsoft"
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
- procedure parameters, defining data types for
- procedures, parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters, defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
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
ms.openlocfilehash: 5a29bab1c18920d293c51d83d4d8cffdcefe936c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="cf966-102">Como definir um parâmetro para um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf966-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="cf966-103">A *parâmetro* permite que o código passe um valor ao procedimento quando ele chama.</span><span class="sxs-lookup"><span data-stu-id="cf966-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="cf966-104">Você declara cada parâmetro para um procedimento da mesma maneira que você declarar uma variável, especificando seu nome e tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="cf966-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="cf966-105">Você também especificar o mecanismo de passagem, e se o parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="cf966-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="cf966-106">Para obter mais informações, consulte [argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="cf966-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="cf966-107">Para definir um parâmetro de procedimento</span><span class="sxs-lookup"><span data-stu-id="cf966-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="cf966-108">Na declaração do procedimento, adicione o nome do parâmetro à lista de parâmetros do procedimento, separando-o de outros parâmetros por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="cf966-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="cf966-109">Decida o tipo de dados do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf966-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="cf966-110">Siga o nome do parâmetro com um `As` cláusula para especificar o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="cf966-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="cf966-111">Decida o mecanismo de passagem que você deseja para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf966-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="cf966-112">Normalmente você passa um parâmetro por valor, a menos que o procedimento seja capaz de alterar seu valor no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="cf966-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="cf966-113">Preceda o nome do parâmetro com [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para especificar o mecanismo de passagem.</span><span class="sxs-lookup"><span data-stu-id="cf966-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="cf966-114">Para obter mais informações, consulte [as diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="cf966-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="cf966-115">Se o parâmetro é opcional, preceda o mecanismo de passagem com [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) e siga o tipo de dados de parâmetro com um sinal de igual (`=`) e um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="cf966-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="cf966-116">O exemplo a seguir define o contorno de uma `Sub` procedimento com três parâmetros.</span><span class="sxs-lookup"><span data-stu-id="cf966-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="cf966-117">As duas primeiras são necessárias e o terceiro é opcional.</span><span class="sxs-lookup"><span data-stu-id="cf966-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="cf966-118">As declarações de parâmetro são separadas na lista de parâmetros por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="cf966-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     <span data-ttu-id="cf966-119">[!code-vb[33 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cf966-119">[!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="cf966-120">O primeiro parâmetro aceita um `customer` objeto, e `updateCustomer` pode atualizar diretamente a variável passada para `c` porque o argumento é passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="cf966-120">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="cf966-121">O procedimento não pode alterar os valores dos dois últimos argumentos porque eles são passados [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="cf966-121">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="cf966-122">Se o código de chamada não fornecer um valor para o `level` parâmetro [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] define como o valor padrão de 0.</span><span class="sxs-lookup"><span data-stu-id="cf966-122">If the calling code does not supply a value for the `level` parameter, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="cf966-123">Se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `Off`, o `As` cláusula é opcional quando você define um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf966-123">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="cf966-124">No entanto, se qualquer outro parâmetro usa um `As` cláusula, todos eles devem usá-lo.</span><span class="sxs-lookup"><span data-stu-id="cf966-124">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="cf966-125">Se a opção de verificação de tipo é `On`, o `As` cláusula é necessária para cada definição de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf966-125">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="cf966-126">Especificar tipos de dados para todos os elementos de programação é conhecido como *tipagem forte*.</span><span class="sxs-lookup"><span data-stu-id="cf966-126">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="cf966-127">Quando você define `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] impõe a tipagem forte.</span><span class="sxs-lookup"><span data-stu-id="cf966-127">When you set `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enforces strong typing.</span></span> <span data-ttu-id="cf966-128">Isso é fortemente recomendado, pelas seguintes razões:</span><span class="sxs-lookup"><span data-stu-id="cf966-128">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="cf966-129">Ela permite suporte IntelliSense para suas variáveis e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="cf966-129">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="cf966-130">Isso permite que você veja suas propriedades e outros membros conforme você digita no seu código.</span><span class="sxs-lookup"><span data-stu-id="cf966-130">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="cf966-131">Ele permite que o compilador execute a verificação de tipo.</span><span class="sxs-lookup"><span data-stu-id="cf966-131">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="cf966-132">Isso ajuda a obter declarações que podem falhar em tempo de execução devido a erros como overflow.</span><span class="sxs-lookup"><span data-stu-id="cf966-132">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="cf966-133">Ele também captura chamadas para métodos em objetos que não oferecem suporte a eles.</span><span class="sxs-lookup"><span data-stu-id="cf966-133">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="cf966-134">Isso resulta em execução mais rápida do seu código.</span><span class="sxs-lookup"><span data-stu-id="cf966-134">It results in faster execution of your code.</span></span> <span data-ttu-id="cf966-135">Uma razão para isso é que, se você não especificar um tipo de dados para um elemento de programação, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador atribui o `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="cf966-135">One reason for this is that if you do not specify a data type for a programming element, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler assigns it the `Object` type.</span></span> <span data-ttu-id="cf966-136">Seu código compilado pode ter que converter entre `Object` e outros tipos de dados, o que reduz o desempenho.</span><span class="sxs-lookup"><span data-stu-id="cf966-136">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf966-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf966-137">See Also</span></span>  
 <span data-ttu-id="cf966-138">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="cf966-138">[Procedures](./index.md) </span></span>  
<span data-ttu-id="cf966-139"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="cf966-139"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="cf966-140"> [Procedimentos de função](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="cf966-140"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="cf966-141"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="cf966-141"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="cf966-142"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cf966-142"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="cf966-143"> [Procedimentos recursivos](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="cf966-143"> [Recursive Procedures](./recursive-procedures.md) </span></span>  
<span data-ttu-id="cf966-144"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="cf966-144"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="cf966-145"> [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="cf966-145"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="cf966-146"> [Programação Orientada a Objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span><span class="sxs-lookup"><span data-stu-id="cf966-146"> [Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span></span>

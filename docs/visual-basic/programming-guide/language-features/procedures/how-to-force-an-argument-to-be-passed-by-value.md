---
title: "Como: forçar um argumento a ser passado por valor (Visual Basic) | Documentos do Microsoft"
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
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], in parentheses
- procedure arguments, in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
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
ms.openlocfilehash: b151c319489ccda357faa082ce0b3c1addad0458
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="0fe7e-102">Como forçar um argumento a ser passado por valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fe7e-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="0fe7e-103">A declaração do procedimento determina o mecanismo de passagem.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="0fe7e-104">Se um parâmetro é declarado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] espera passar o argumento correspondente por referência.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="0fe7e-105">Isso permite que o procedimento alterar o valor do elemento de programação subjacente o argumento o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="0fe7e-106">Se você desejar proteger o elemento subjacente contra alteração, você pode substituir o `ByRef` mecanismo de passagem no procedimento de chamada, colocando o nome do argumento entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="0fe7e-107">Esses parênteses são adicionais aos parênteses envolvendo a lista de argumentos na chamada.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="0fe7e-108">O código de chamada não pode substituir um [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mecanismo.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="0fe7e-109">Para forçar um argumento a ser passado por valor</span><span class="sxs-lookup"><span data-stu-id="0fe7e-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="0fe7e-110">Se o parâmetro correspondente é declarado `ByVal` no procedimento, você não precisa executar etapas adicionais.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="0fe7e-111">já espera passar o argumento por valor.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-111"> already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="0fe7e-112">Se o parâmetro correspondente é declarado `ByRef` no procedimento, coloque o argumento entre parênteses na chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fe7e-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0fe7e-113">Example</span></span>  
 <span data-ttu-id="0fe7e-114">O exemplo a seguir substitui um `ByRef` declaração de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="0fe7e-115">Na chamada de força `ByVal`, observe os dois níveis de parênteses.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 <span data-ttu-id="0fe7e-116">[!code-vb[VbVbcnProcedures&#39;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0fe7e-116">[!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]</span></span>  
  
 <span data-ttu-id="0fe7e-117">[!code-vb[40 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0fe7e-117">[!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]</span></span>  
  
 <span data-ttu-id="0fe7e-118">Quando `str` é colocado entre parênteses extras na lista de argumentos, o `setNewString` procedimento não pode alterar o valor no código de chamada, e `MsgBox` exibe "Não pode ser substituído se passado ByVal".</span><span class="sxs-lookup"><span data-stu-id="0fe7e-118">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="0fe7e-119">Quando `str` não é colocado entre parênteses extras, o procedimento pode alterá-lo, e `MsgBox` exibe "Este é um novo valor para o argumento inString."</span><span class="sxs-lookup"><span data-stu-id="0fe7e-119">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0fe7e-120">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0fe7e-120">Compiling the Code</span></span>  
 <span data-ttu-id="0fe7e-121">Quando uma variável é passada por referência, você deve usar o `ByRef` palavra-chave para especificar esse mecanismo.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-121">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="0fe7e-122">O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-122">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="0fe7e-123">No entanto, é boa prática incluir de programação a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave com cada parâmetro declarado.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-123">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="0fe7e-124">Isso torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-124">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0fe7e-125">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="0fe7e-125">Robust Programming</span></span>  
 <span data-ttu-id="0fe7e-126">Se um procedimento declara um parâmetro [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), a execução correta do código pode depender de poder alterar o elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-126">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="0fe7e-127">Se o código de chamada substitui esse mecanismo de chamada, colocando o argumento entre parênteses, ou se ele passa um argumento não modificável, o procedimento não pode alterar o elemento subjacente.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-127">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="0fe7e-128">Isso pode produzir resultados inesperados no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-128">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0fe7e-129">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0fe7e-129">.NET Framework Security</span></span>  
 <span data-ttu-id="0fe7e-130">Sempre há um risco potencial em permitir que um procedimento alterar o valor subjacente um argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-130">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="0fe7e-131">Verifique se você espera que esse valor seja alterado e esteja preparado para verificá-lo para validade antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="0fe7e-131">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe7e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fe7e-132">See Also</span></span>  
 <span data-ttu-id="0fe7e-133">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-133">[Procedures](./index.md) </span></span>  
<span data-ttu-id="0fe7e-134"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-134"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="0fe7e-135"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-135"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="0fe7e-136"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-136"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="0fe7e-137"> [Diferenças entre argumentos modificável e não modificável](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-137"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="0fe7e-138"> [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-138"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="0fe7e-139"> [Como: alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-139"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="0fe7e-140"> [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-140"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="0fe7e-141"> [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="0fe7e-141"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="0fe7e-142"> [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="0fe7e-142"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>

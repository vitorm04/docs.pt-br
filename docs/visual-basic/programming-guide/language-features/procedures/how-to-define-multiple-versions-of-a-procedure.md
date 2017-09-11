---
title: "Como: definir várias versões de um procedimento (Visual Basic) | Documentos do Microsoft"
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
- procedures, defining
- Visual Basic code, procedures
- procedures, overloading
- procedures, multiple versions
- procedure overloading, multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
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
ms.openlocfilehash: f4296ba3a78316b70011bcca18f7071716f3c90d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="5addb-102">Como definir várias versões de um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5addb-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="5addb-103">Você pode definir um procedimento em múltiplas versões por *sobrecarga* -lo, usando o mesmo nome mas uma lista de parâmetros diferentes para cada versão.</span><span class="sxs-lookup"><span data-stu-id="5addb-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="5addb-104">O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem diferenciá-los pelo nome.</span><span class="sxs-lookup"><span data-stu-id="5addb-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="5addb-105">Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="5addb-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="5addb-106">Para definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="5addb-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="5addb-107">Escrever um `Sub` ou `Function` uma instrução de declaração para cada versão do procedimento que você deseja definir.</span><span class="sxs-lookup"><span data-stu-id="5addb-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="5addb-108">Use o mesmo nome do procedimento em cada declaração.</span><span class="sxs-lookup"><span data-stu-id="5addb-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="5addb-109">Preceder o `Sub` ou `Function` palavra-chave em cada declaração com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5addb-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="5addb-110">Opcionalmente, você pode omitir `Overloads` em declarações, mas se você incluí-lo em qualquer um das declarações, você deve incluí-lo em cada declaração.</span><span class="sxs-lookup"><span data-stu-id="5addb-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="5addb-111">Após cada instrução de declaração, escreva código de procedimento para manipular a ocorrência específica onde o código de chamada fornece argumentos correspondentes a lista de parâmetros da versão.</span><span class="sxs-lookup"><span data-stu-id="5addb-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="5addb-112">Você não precisa testar para quais parâmetros o código de chamada forneceu.</span><span class="sxs-lookup"><span data-stu-id="5addb-112">You do not have to test for which parameters the calling code has supplied.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5addb-113">passa o controle para a versão correspondente do seu procedimento.</span><span class="sxs-lookup"><span data-stu-id="5addb-113"> passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="5addb-114">Cada versão do procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="5addb-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5addb-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5addb-115">Example</span></span>  
 <span data-ttu-id="5addb-116">O exemplo a seguir define uma `Sub` procedimento para lançar uma transação contra um saldo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5addb-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="5addb-117">Ele usa o `Overloads` palavra-chave para definir duas versões do procedimento, uma que aceita o cliente por nome e a outra pelo número de conta.</span><span class="sxs-lookup"><span data-stu-id="5addb-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 <span data-ttu-id="5addb-118">[!code-vb[VbVbcnProcedures&#72;](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5addb-118">[!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]</span></span>  
  
 <span data-ttu-id="5addb-119">O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, use a mesma instrução de chamada em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="5addb-119">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="5addb-120">Para obter informações sobre como chamar essas versões do `post` procedimento, consulte [como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="5addb-120">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5addb-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5addb-121">Compiling the Code</span></span>  
 <span data-ttu-id="5addb-122">Verifique se que cada uma das suas versões sobrecarregadas tem o mesmo nome de procedimento, mas uma lista de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="5addb-122">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5addb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5addb-123">See Also</span></span>  
 <span data-ttu-id="5addb-124">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="5addb-124">[Procedures](./index.md) </span></span>  
<span data-ttu-id="5addb-125"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="5addb-125"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="5addb-126"> [Procedimentos de solução de problemas](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="5addb-126"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="5addb-127"> [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="5addb-127"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="5addb-128"> [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="5addb-128"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="5addb-129"> [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="5addb-129"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="5addb-130"> [Resolução de Sobrecarga](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="5addb-130"> [Overload Resolution](./overload-resolution.md)</span></span>

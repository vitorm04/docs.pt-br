---
title: Como definir várias versões de um procedimento (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: a4d0c5bbb07dd5433ff62179fc10a6274bf19364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649806"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="673d0-102">Como definir várias versões de um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="673d0-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="673d0-103">Você pode definir um procedimento em várias versões por *sobrecarga* -la, usando o mesmo nome mas uma lista de parâmetros diferentes para cada versão.</span><span class="sxs-lookup"><span data-stu-id="673d0-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="673d0-104">O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem diferenciá-los por nome.</span><span class="sxs-lookup"><span data-stu-id="673d0-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="673d0-105">Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="673d0-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="673d0-106">Para definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="673d0-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="673d0-107">Gravar um `Sub` ou `Function` declaração para cada versão do procedimento que você deseja definir.</span><span class="sxs-lookup"><span data-stu-id="673d0-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="673d0-108">Use o mesmo nome do procedimento em cada declaração.</span><span class="sxs-lookup"><span data-stu-id="673d0-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="673d0-109">Preceder o `Sub` ou `Function` palavra-chave em cada declaração com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="673d0-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="673d0-110">Opcionalmente, você pode omitir `Overloads` em declarações, mas se você incluir em qualquer uma das declarações, você deve incluí-lo em cada declaração.</span><span class="sxs-lookup"><span data-stu-id="673d0-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="673d0-111">Após cada instrução de declaração, grave o código de procedimento para manipular o caso específico em que o código de chamada fornece argumentos correspondentes a lista de parâmetros desta versão.</span><span class="sxs-lookup"><span data-stu-id="673d0-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="673d0-112">Você não precisa testar para quais parâmetros forneceu o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="673d0-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="673d0-113">Visual Basic passa o controle para a versão correspondente do seu procedimento.</span><span class="sxs-lookup"><span data-stu-id="673d0-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="673d0-114">Cada versão do procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="673d0-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="673d0-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="673d0-115">Example</span></span>  
 <span data-ttu-id="673d0-116">O exemplo a seguir define uma `Sub` procedimento para lançar uma transação contra um saldo do cliente.</span><span class="sxs-lookup"><span data-stu-id="673d0-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="673d0-117">Ele usa o `Overloads` palavra-chave para definir duas versões do procedimento, uma que aceita o cliente por nome e a outra pelo número de conta.</span><span class="sxs-lookup"><span data-stu-id="673d0-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 <span data-ttu-id="673d0-118">O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, use a mesma instrução de chamada em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="673d0-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="673d0-119">Para obter informações sobre como chamar essas versões do `post` procedimento, consulte [como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="673d0-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="673d0-120">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="673d0-120">Compiling the Code</span></span>  
 <span data-ttu-id="673d0-121">Verifique se que cada uma das suas versões sobrecarregadas tem o mesmo nome de procedimento, mas uma lista de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="673d0-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673d0-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="673d0-122">See Also</span></span>  
 [<span data-ttu-id="673d0-123">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="673d0-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="673d0-124">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="673d0-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="673d0-125">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="673d0-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="673d0-126">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="673d0-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="673d0-127">Como sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="673d0-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="673d0-128">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="673d0-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="673d0-129">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="673d0-129">Overload Resolution</span></span>](./overload-resolution.md)

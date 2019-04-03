---
title: 'Como: Definir várias versões de um procedimento (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: c31c9ad05af04aec5dc41790aea530c62611f500
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841156"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="73f57-102">Como: Definir várias versões de um procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73f57-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="73f57-103">Você pode definir um procedimento em várias versões por *sobrecarga* -lo, usando o mesmo nome mas uma lista de parâmetros diferentes para cada versão.</span><span class="sxs-lookup"><span data-stu-id="73f57-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="73f57-104">O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem a necessidade para diferenciá-los por nome.</span><span class="sxs-lookup"><span data-stu-id="73f57-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="73f57-105">Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="73f57-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="73f57-106">Para definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="73f57-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="73f57-107">Gravar uma `Sub` ou `Function` instrução de declaração para cada versão do procedimento que você deseja definir.</span><span class="sxs-lookup"><span data-stu-id="73f57-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="73f57-108">Use o mesmo nome do procedimento em cada declaração.</span><span class="sxs-lookup"><span data-stu-id="73f57-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="73f57-109">Preceda a `Sub` ou `Function` palavra-chave em cada declaração com o [sobrecarrega](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="73f57-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="73f57-110">Opcionalmente, você pode omitir `Overloads` em declarações, mas se você incluí-lo em qualquer uma das declarações, você deve incluí-lo em cada declaração.</span><span class="sxs-lookup"><span data-stu-id="73f57-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="73f57-111">Após cada instrução de declaração, escreva um código de procedimento para manipular o caso específico em que o código de chamada fornece argumentos correspondentes a lista de parâmetros desta versão.</span><span class="sxs-lookup"><span data-stu-id="73f57-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="73f57-112">Você não precisa testar para quais parâmetros o código de chamada forneceu.</span><span class="sxs-lookup"><span data-stu-id="73f57-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="73f57-113">Visual Basic passa o controle para a versão correspondente do seu procedimento.</span><span class="sxs-lookup"><span data-stu-id="73f57-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="73f57-114">Cada versão do procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="73f57-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73f57-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73f57-115">Example</span></span>  
 <span data-ttu-id="73f57-116">O exemplo a seguir define uma `Sub` procedimento para lançar uma transação em relação ao saldo do cliente.</span><span class="sxs-lookup"><span data-stu-id="73f57-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="73f57-117">Ele usa o `Overloads` palavra-chave para definir duas versões do procedimento, uma que aceita o cliente por nome e a outra pelo número de conta.</span><span class="sxs-lookup"><span data-stu-id="73f57-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="73f57-118">O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, use a mesma instrução de chamada em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="73f57-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="73f57-119">Para obter informações sobre como chamar essas versões dos `post` procedimento, consulte [como: Chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="73f57-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73f57-120">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="73f57-120">Compiling the Code</span></span>  
 <span data-ttu-id="73f57-121">Verifique se que cada uma das suas versões sobrecarregadas tem o mesmo nome de procedimento, mas uma lista de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="73f57-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f57-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f57-122">See also</span></span>

- [<span data-ttu-id="73f57-123">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="73f57-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="73f57-124">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="73f57-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="73f57-125">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="73f57-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="73f57-126">Como: Sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="73f57-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="73f57-127">Como: Sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="73f57-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="73f57-128">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="73f57-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="73f57-129">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="73f57-129">Overload Resolution</span></span>](./overload-resolution.md)

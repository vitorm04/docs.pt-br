---
title: Como chamar um procedimento sobrecarregado
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: d983f5f6183c33141079ed35171f7a73f254450f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340203"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="7e36b-102">Como chamar um procedimento sobrecarregado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e36b-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="7e36b-103">A vantagem de sobrecarregar um procedimento é a flexibilidade da chamada.</span><span class="sxs-lookup"><span data-stu-id="7e36b-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="7e36b-104">O código de chamada pode obter as informações necessárias para passar para o procedimento e, em seguida, chamar um único nome de procedimento, independentemente de quais argumentos ele está passando.</span><span class="sxs-lookup"><span data-stu-id="7e36b-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="7e36b-105">Para chamar um procedimento que tem mais de uma versão definida</span><span class="sxs-lookup"><span data-stu-id="7e36b-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="7e36b-106">No código de chamada, determine quais dados passar para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="7e36b-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="7e36b-107">Escreva a chamada de procedimento da maneira normal, apresentando os dados na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="7e36b-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="7e36b-108">Certifique-se de que os argumentos correspondam à lista de parâmetros em uma das versões definidas para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="7e36b-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="7e36b-109">Você não precisa determinar qual versão do procedimento chamar.</span><span class="sxs-lookup"><span data-stu-id="7e36b-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="7e36b-110">Visual Basic passa o controle para a versão correspondente à sua lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="7e36b-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="7e36b-111">O exemplo a seguir chama o procedimento `post` declarado em [como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="7e36b-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="7e36b-112">Ele obtém a identificação do cliente, determina se é uma `String` ou uma `Integer`e, em qualquer caso, chama o mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="7e36b-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="7e36b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e36b-113">See also</span></span>

- [<span data-ttu-id="7e36b-114">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="7e36b-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7e36b-115">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="7e36b-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7e36b-116">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="7e36b-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="7e36b-117">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="7e36b-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="7e36b-118">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="7e36b-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="7e36b-119">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="7e36b-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="7e36b-120">Como sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e36b-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="7e36b-121">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="7e36b-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="7e36b-122">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="7e36b-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="7e36b-123">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="7e36b-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)

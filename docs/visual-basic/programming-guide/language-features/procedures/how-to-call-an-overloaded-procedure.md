---
title: 'Como: chamar um procedimento sobrecarregado (Visual Basic) | Documentos do Microsoft'
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
- Visual Basic code, procedures
- procedures, overloading
- procedures, calling
- procedures, multiple versions
- procedure calls, overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
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
ms.openlocfilehash: 777df0cc81a4e0518773a0e8cc98d590d1c0cf0d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="37116-102">Como chamar um procedimento sobrecarregado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37116-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="37116-103">A vantagem de sobrecarregar um procedimento é na flexibilidade da chamada.</span><span class="sxs-lookup"><span data-stu-id="37116-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="37116-104">O código de chamada pode obter as informações necessárias para passar para o procedimento e, em seguida, chamar um único nome de procedimento, não importa quais argumentos ele está passando.</span><span class="sxs-lookup"><span data-stu-id="37116-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="37116-105">Para chamar um procedimento que tem mais de uma versão definida</span><span class="sxs-lookup"><span data-stu-id="37116-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="37116-106">No código de chamada, determine quais dados devem passar para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="37116-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="37116-107">Escreva a chamada de procedimento da maneira normal, apresentando os dados na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="37116-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="37116-108">Certifique-se de que os argumentos correspondam à lista de parâmetro em uma das versões definidas para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="37116-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="37116-109">Você não precisa determinar qual versão do procedimento a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="37116-109">You do not have to determine which version of the procedure to call.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="37116-110">passa o controle para a versão correspondente a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="37116-110"> passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="37116-111">A exemplo a seguir chama o `post` procedimento declarado em [como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="37116-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="37116-112">Obtém a identificação do cliente, determina se é um `String` ou um `Integer`e, em seguida, em ambos os casos chama o mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="37116-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     <span data-ttu-id="37116-113">[!code-vb[56 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="37116-113">[!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="37116-114">[!code-vb[VbVbcnProcedures&#57;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="37116-114">[!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37116-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37116-115">See Also</span></span>  
 <span data-ttu-id="37116-116">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="37116-116">[Procedures](./index.md) </span></span>  
<span data-ttu-id="37116-117"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="37116-117"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="37116-118"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="37116-118"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="37116-119"> [Procedimentos de solução de problemas](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="37116-119"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="37116-120"> [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="37116-120"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="37116-121"> [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="37116-121"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="37116-122"> [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="37116-122"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="37116-123"> [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="37116-123"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="37116-124"> [Resolução de sobrecarga](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="37116-124"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="37116-125"> [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="37116-125"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>

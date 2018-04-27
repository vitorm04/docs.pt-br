---
title: '&#39;Como qualquer&#39; não há suporte para &#39;Declare&#39; instruções'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8146e339ac5cb005b99c9a1e02f1cd248c4558b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="90e61-102">&#39;Como qualquer&#39; não há suporte para &#39;Declare&#39; instruções</span><span class="sxs-lookup"><span data-stu-id="90e61-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="90e61-103">O `Any` tipo de dados foi usado com `Declare` instruções no Visual Basic 6.0 e versões anteriores para permitir o uso dos argumentos que pode conter qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="90e61-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="90e61-104">Visual Basic oferece suporte à sobrecarga, porém e assim torna o `Any` obsoleto de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="90e61-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="90e61-105">**ID do erro:** BC30828</span><span class="sxs-lookup"><span data-stu-id="90e61-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="90e61-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="90e61-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="90e61-107">Declarar parâmetros do tipo específico que você deseja usar; Por exemplo.</span><span class="sxs-lookup"><span data-stu-id="90e61-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="90e61-108">Use o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para especificar `As Any` quando `Void*` é esperado pelo procedimento que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="90e61-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="90e61-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90e61-109">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="90e61-110">Instruções passo a passo: chamando APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="90e61-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="90e61-111">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="90e61-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="90e61-112">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="90e61-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)

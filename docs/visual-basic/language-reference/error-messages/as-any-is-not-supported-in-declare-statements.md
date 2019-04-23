---
title: "'As Any' não é suportado em instruções 'Declare'"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 3593f238c72cbcce911c72e42552d6a75188b628
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310688"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a><span data-ttu-id="e5bee-102">'As Any' não é suportado em instruções 'Declare'</span><span class="sxs-lookup"><span data-stu-id="e5bee-102">'As Any' is not supported in 'Declare' statements</span></span>
<span data-ttu-id="e5bee-103">O `Any` tipo de dados foi usado com `Declare` instruções no Visual Basic 6.0 e versões anteriores, a fim de permitir o uso de argumentos que pode conter qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e5bee-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="e5bee-104">Visual Basic oferece suporte a sobrecarga, no entanto e assim torna o `Any` obsoleto de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e5bee-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="e5bee-105">**ID do erro:** BC30828</span><span class="sxs-lookup"><span data-stu-id="e5bee-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5bee-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e5bee-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e5bee-107">Declarar parâmetros do tipo específico que você deseja usar; Por exemplo.</span><span class="sxs-lookup"><span data-stu-id="e5bee-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2. <span data-ttu-id="e5bee-108">Use o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para especificar `As Any` quando `Void*` é esperado pelo procedimento sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="e5bee-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a><span data-ttu-id="e5bee-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5bee-109">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e5bee-110">Passo a passo: fazer chamadas de APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="e5bee-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="e5bee-111">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="e5bee-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="e5bee-112">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="e5bee-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)

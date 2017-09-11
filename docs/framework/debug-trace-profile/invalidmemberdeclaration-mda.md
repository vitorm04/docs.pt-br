---
title: MDA invalidMemberDeclaration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 34db255e3e04776123d30ad06dc3026c4e75addd
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="5df1c-102">MDA invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="5df1c-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="5df1c-103">O MDA (Assistente de Depuração Gerenciado) de `invalidMemberDeclaration` é ativado para relatar um erro que ocorre ao determinar como realizar marshaling dos parâmetros de um membro a ser chamado do COM.</span><span class="sxs-lookup"><span data-stu-id="5df1c-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5df1c-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="5df1c-104">Symptoms</span></span>  
 <span data-ttu-id="5df1c-105">Uma falha de HRESULT é retornada ao COM sem o método gerenciado ter sido chamado.</span><span class="sxs-lookup"><span data-stu-id="5df1c-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5df1c-106">Causa</span><span class="sxs-lookup"><span data-stu-id="5df1c-106">Cause</span></span>  
 <span data-ttu-id="5df1c-107">Isso ocorre provavelmente devido a um atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> incompatível em um dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5df1c-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5df1c-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="5df1c-108">Resolution</span></span>  
 <span data-ttu-id="5df1c-109">Especifique atributos <xref:System.Runtime.InteropServices.MarshalAsAttribute> válidos nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5df1c-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5df1c-110">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5df1c-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="5df1c-111">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="5df1c-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5df1c-112">Saída</span><span class="sxs-lookup"><span data-stu-id="5df1c-112">Output</span></span>  
 <span data-ttu-id="5df1c-113">Uma mensagem informativa contendo o nome do membro, o nome do tipo e a mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="5df1c-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5df1c-114">Configuração</span><span class="sxs-lookup"><span data-stu-id="5df1c-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5df1c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5df1c-115">See Also</span></span>  
 <span data-ttu-id="5df1c-116"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="5df1c-116"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="5df1c-117">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="5df1c-117">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 [<span data-ttu-id="5df1c-118">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5df1c-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)


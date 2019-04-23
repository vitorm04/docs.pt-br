---
title: MDA invalidMemberDeclaration
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e5b4cb4a04a79a748f4ea2292bac67a88a6e9f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131281"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="bdb73-102">MDA invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="bdb73-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="bdb73-103">O MDA (Assistente de Depuração Gerenciado) de `invalidMemberDeclaration` é ativado para relatar um erro que ocorre ao determinar como realizar marshaling dos parâmetros de um membro a ser chamado do COM.</span><span class="sxs-lookup"><span data-stu-id="bdb73-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bdb73-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="bdb73-104">Symptoms</span></span>  
 <span data-ttu-id="bdb73-105">Uma falha de HRESULT é retornada ao COM sem o método gerenciado ter sido chamado.</span><span class="sxs-lookup"><span data-stu-id="bdb73-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bdb73-106">Causa</span><span class="sxs-lookup"><span data-stu-id="bdb73-106">Cause</span></span>  
 <span data-ttu-id="bdb73-107">Isso ocorre provavelmente devido a um atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> incompatível em um dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bdb73-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bdb73-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="bdb73-108">Resolution</span></span>  
 <span data-ttu-id="bdb73-109">Especifique atributos <xref:System.Runtime.InteropServices.MarshalAsAttribute> válidos nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bdb73-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bdb73-110">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bdb73-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="bdb73-111">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="bdb73-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bdb73-112">Saída</span><span class="sxs-lookup"><span data-stu-id="bdb73-112">Output</span></span>  
 <span data-ttu-id="bdb73-113">Uma mensagem informativa contendo o nome do membro, o nome do tipo e a mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="bdb73-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bdb73-114">Configuração</span><span class="sxs-lookup"><span data-stu-id="bdb73-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bdb73-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdb73-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="bdb73-116">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="bdb73-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="bdb73-117">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="bdb73-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

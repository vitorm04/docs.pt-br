---
title: MDA invalidMemberDeclaration
description: Examine o assistente de depuração gerenciada do invalidMemberDeclaration, que será invocado se um HRESULT de falha for retornado para COM sem chamar o método gerenciado.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 5dbfba2baec3263d91746c06379438e97a81f005
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051708"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="961cc-103">MDA invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="961cc-103">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="961cc-104">O MDA (Assistente de Depuração Gerenciado) de `invalidMemberDeclaration` é ativado para relatar um erro que ocorre ao determinar como realizar marshaling dos parâmetros de um membro a ser chamado do COM.</span><span class="sxs-lookup"><span data-stu-id="961cc-104">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="961cc-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="961cc-105">Symptoms</span></span>  
 <span data-ttu-id="961cc-106">Uma falha de HRESULT é retornada ao COM sem o método gerenciado ter sido chamado.</span><span class="sxs-lookup"><span data-stu-id="961cc-106">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="961cc-107">Causa</span><span class="sxs-lookup"><span data-stu-id="961cc-107">Cause</span></span>  
 <span data-ttu-id="961cc-108">Isso ocorre provavelmente devido a um atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> incompatível em um dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="961cc-108">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="961cc-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="961cc-109">Resolution</span></span>  
 <span data-ttu-id="961cc-110">Especifique atributos <xref:System.Runtime.InteropServices.MarshalAsAttribute> válidos nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="961cc-110">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="961cc-111">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="961cc-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="961cc-112">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="961cc-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="961cc-113">Saída</span><span class="sxs-lookup"><span data-stu-id="961cc-113">Output</span></span>  
 <span data-ttu-id="961cc-114">Uma mensagem informativa contendo o nome do membro, o nome do tipo e a mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="961cc-114">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="961cc-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="961cc-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="961cc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="961cc-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="961cc-117">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="961cc-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="961cc-118">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="961cc-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)

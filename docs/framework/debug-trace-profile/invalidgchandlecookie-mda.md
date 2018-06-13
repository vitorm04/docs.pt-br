---
title: MDA invalidGCHandleCookie
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f1542cf9d0568fe2ec35c046c358b7249231d42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392899"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="a6efa-102">MDA invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="a6efa-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="a6efa-103">O MDA (Assistente de Depuração Gerenciado) de `invalidGCHandleCookie` é ativado quando há uma tentativa de conversão de um cookie <xref:System.IntPtr> inválido em um <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="a6efa-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a6efa-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="a6efa-104">Symptoms</span></span>  
 <span data-ttu-id="a6efa-105">Um comportamento indefinido, tal como violações de acesso e corrupção de memória, durante a tentativa de usar ou recuperar um <xref:System.Runtime.InteropServices.GCHandle> de um <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="a6efa-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a6efa-106">Causa</span><span class="sxs-lookup"><span data-stu-id="a6efa-106">Cause</span></span>  
 <span data-ttu-id="a6efa-107">O cookie é provavelmente inválido porque ele não foi criado originalmente de um <xref:System.Runtime.InteropServices.GCHandle>, representa um <xref:System.Runtime.InteropServices.GCHandle> que já foi liberado, é um cookie para um <xref:System.Runtime.InteropServices.GCHandle> em um domínio do aplicativo diferente ou então realizou-se marshaling dele para código nativo como um <xref:System.Runtime.InteropServices.GCHandle> mas ele foi passado de volta para o CLR como um <xref:System.IntPtr>, ponto em que foi tentada uma conversão.</span><span class="sxs-lookup"><span data-stu-id="a6efa-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a6efa-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="a6efa-108">Resolution</span></span>  
 <span data-ttu-id="a6efa-109">Especifique um cookie <xref:System.IntPtr> válido para o <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="a6efa-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a6efa-110">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a6efa-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="a6efa-111">Quando esse MDA está habilitado, o depurador não é capaz de rastrear as raízes de volta para seus objetos porque os valores de cookie passados de volta são diferentes daqueles retornados quando o MDA não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a6efa-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a6efa-112">Saída</span><span class="sxs-lookup"><span data-stu-id="a6efa-112">Output</span></span>  
 <span data-ttu-id="a6efa-113">O valor do cookie <xref:System.IntPtr> inválido é relatado.</span><span class="sxs-lookup"><span data-stu-id="a6efa-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a6efa-114">Configuração</span><span class="sxs-lookup"><span data-stu-id="a6efa-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6efa-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6efa-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>  
 <xref:System.Runtime.InteropServices.GCHandle>  
 [<span data-ttu-id="a6efa-116">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="a6efa-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

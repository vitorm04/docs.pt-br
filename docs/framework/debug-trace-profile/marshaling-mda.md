---
title: MDA marshaling
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b1a1607e96ad9953a409d79fd265ced994cece2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854138"
---
# <a name="marshaling-mda"></a><span data-ttu-id="f6ddf-102">MDA marshaling</span><span class="sxs-lookup"><span data-stu-id="f6ddf-102">marshaling MDA</span></span>
<span data-ttu-id="f6ddf-103">O MDA (Assistente de Depuração Gerenciado) de `marshaling` é ativado quando o CLR define informações de marshaling para um parâmetro de método ou um campo de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="f6ddf-104">Esse MDA não funciona para assemblies compilados por JIT.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f6ddf-105">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f6ddf-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="f6ddf-106">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f6ddf-107">Saída</span><span class="sxs-lookup"><span data-stu-id="f6ddf-107">Output</span></span>  
 <span data-ttu-id="f6ddf-108">O MDA exibe o tipo do parâmetro ou campo nos contextos gerenciado e não gerenciado, bem como a estrutura ou o método que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="f6ddf-109">A seguir está um exemplo da saída de um campo:</span><span class="sxs-lookup"><span data-stu-id="f6ddf-109">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="f6ddf-110">Configuração</span><span class="sxs-lookup"><span data-stu-id="f6ddf-110">Configuration</span></span>  
 <span data-ttu-id="f6ddf-111">A configuração de MDA permite que você filtre as informações de marshaling relatadas com base no campo envolvido ou em nomes de método.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="f6ddf-112">O exemplo a seguir mostra o uso dos elementos `methodFilter`, `fieldFilter` e `match` para especificar filtros.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="f6ddf-113">A definição `name` do atributo como um asterisco\*() corresponderá a tudo.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6ddf-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6ddf-114">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f6ddf-115">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="f6ddf-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f6ddf-116">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="f6ddf-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

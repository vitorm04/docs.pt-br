---
title: MDA marshaling
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 83b621f78e3ba4641540f6125ed14d600cc292d1
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="marshaling-mda"></a><span data-ttu-id="5289b-102">MDA marshaling</span><span class="sxs-lookup"><span data-stu-id="5289b-102">marshaling MDA</span></span>
<span data-ttu-id="5289b-103">O MDA (Assistente de Depuração Gerenciado) de `marshaling` é ativado quando o CLR define informações de marshaling para um parâmetro de método ou um campo de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="5289b-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="5289b-104">Esse MDA não funciona para assemblies compilados por JIT.</span><span class="sxs-lookup"><span data-stu-id="5289b-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5289b-105">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5289b-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="5289b-106">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="5289b-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5289b-107">Saída</span><span class="sxs-lookup"><span data-stu-id="5289b-107">Output</span></span>  
 <span data-ttu-id="5289b-108">O MDA exibe o tipo do parâmetro ou campo nos contextos gerenciado e não gerenciado, bem como a estrutura ou o método que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="5289b-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="5289b-109">A seguir está um exemplo da saída de um campo:</span><span class="sxs-lookup"><span data-stu-id="5289b-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="5289b-110">Configuração</span><span class="sxs-lookup"><span data-stu-id="5289b-110">Configuration</span></span>  
 <span data-ttu-id="5289b-111">A configuração de MDA permite que você filtre as informações de marshaling relatadas com base no campo envolvido ou em nomes de método.</span><span class="sxs-lookup"><span data-stu-id="5289b-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="5289b-112">O exemplo a seguir mostra o uso dos elementos `methodFilter`, `fieldFilter` e `match` para especificar filtros.</span><span class="sxs-lookup"><span data-stu-id="5289b-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="5289b-113">Definir o atributo `name` como um asterisco (\*) corresponderá a tudo.</span><span class="sxs-lookup"><span data-stu-id="5289b-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5289b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5289b-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="5289b-115">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="5289b-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="5289b-116">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5289b-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

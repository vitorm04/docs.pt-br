---
title: MDA memberInfoCacheCreation
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ebc449985a8e2617b278f04c91d243ca11b637e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145196"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="bc87d-102">MDA memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="bc87d-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="bc87d-103">O MDA (Assistente de Depuração Gerenciado) de `memberInfoCacheCreation` é ativado quando um cache de <xref:System.Reflection.MemberInfo> é criado.</span><span class="sxs-lookup"><span data-stu-id="bc87d-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="bc87d-104">Isso é uma indicação forte de um programa que está fazendo uso de recursos de reflexão com consumo elevado de recursos computacionais.</span><span class="sxs-lookup"><span data-stu-id="bc87d-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bc87d-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="bc87d-105">Symptoms</span></span>  
 <span data-ttu-id="bc87d-106">O conjunto de trabalho de um programa aumenta porque o programa está usando reflexão com consumo elevado de recursos.</span><span class="sxs-lookup"><span data-stu-id="bc87d-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bc87d-107">Causa</span><span class="sxs-lookup"><span data-stu-id="bc87d-107">Cause</span></span>  
 <span data-ttu-id="bc87d-108">Operações de reflexão que envolvem objetos <xref:System.Reflection.MemberInfo> são consideradas grandes consumidoras de recursos porque elas devem ler os metadados que são armazenados em páginas frias e, em geral, eles indicam que o programa está usando algum tipo de cenário de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="bc87d-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bc87d-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="bc87d-109">Resolution</span></span>  
 <span data-ttu-id="bc87d-110">Você pode determinar o local em que a reflexão está sendo usada em seu programa habilitando esse MDA e, em seguida, executando o código em um depurador ou anexando com um depurador quando o MDA é ativado.</span><span class="sxs-lookup"><span data-stu-id="bc87d-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="bc87d-111">Em um depurador, você obterá um rastreamento de pilha mostrando o local em que o cache <xref:System.Reflection.MemberInfo> foi criado e, desse ponto em diante, você poderá determinar o local em que o programa está usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="bc87d-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="bc87d-112">A resolução depende dos objetivos do código.</span><span class="sxs-lookup"><span data-stu-id="bc87d-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="bc87d-113">Esse MDA alerta você de que o programa tem um cenário de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="bc87d-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="bc87d-114">Você talvez queira determinar se você pode substituir um cenário de associação precoce ou considerar o desempenho do cenário de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="bc87d-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bc87d-115">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bc87d-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="bc87d-116">Esse MDA é ativado para cada cache <xref:System.Reflection.MemberInfo> criado.</span><span class="sxs-lookup"><span data-stu-id="bc87d-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="bc87d-117">O impacto de desempenho é negligenciável.</span><span class="sxs-lookup"><span data-stu-id="bc87d-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bc87d-118">Saída</span><span class="sxs-lookup"><span data-stu-id="bc87d-118">Output</span></span>  
 <span data-ttu-id="bc87d-119">O MDA gera uma mensagem indicando que o cache <xref:System.Reflection.MemberInfo> foi criado.</span><span class="sxs-lookup"><span data-stu-id="bc87d-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="bc87d-120">Use um depurador para obter um rastreamento de pilha mostrando o local em que o programa está usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="bc87d-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bc87d-121">Configuração</span><span class="sxs-lookup"><span data-stu-id="bc87d-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="bc87d-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc87d-122">Example</span></span>  
 <span data-ttu-id="bc87d-123">Esse código de exemplo ativará o MDA `memberInfoCacheCreation`.</span><span class="sxs-lookup"><span data-stu-id="bc87d-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc87d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc87d-124">See Also</span></span>  
 <xref:System.Reflection.MemberInfo>  
 [<span data-ttu-id="bc87d-125">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="bc87d-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

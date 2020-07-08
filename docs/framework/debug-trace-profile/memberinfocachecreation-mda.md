---
title: MDA memberInfoCacheCreation
description: Entenda o MDA (Assistente de depuração gerenciada) do memberInfoCacheCreation no .NET, que é ativado quando um cache MemberInfo é criado.
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
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051136"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="040b2-103">MDA memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="040b2-103">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="040b2-104">O MDA (Assistente de Depuração Gerenciado) de `memberInfoCacheCreation` é ativado quando um cache de <xref:System.Reflection.MemberInfo> é criado.</span><span class="sxs-lookup"><span data-stu-id="040b2-104">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="040b2-105">Isso é uma indicação forte de um programa que está fazendo uso de recursos de reflexão com consumo elevado de recursos computacionais.</span><span class="sxs-lookup"><span data-stu-id="040b2-105">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="040b2-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="040b2-106">Symptoms</span></span>  
 <span data-ttu-id="040b2-107">O conjunto de trabalho de um programa aumenta porque o programa está usando reflexão com consumo elevado de recursos.</span><span class="sxs-lookup"><span data-stu-id="040b2-107">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="040b2-108">Causa</span><span class="sxs-lookup"><span data-stu-id="040b2-108">Cause</span></span>  
 <span data-ttu-id="040b2-109">Operações de reflexão que envolvem objetos <xref:System.Reflection.MemberInfo> são consideradas grandes consumidoras de recursos porque elas devem ler os metadados que são armazenados em páginas frias e, em geral, eles indicam que o programa está usando algum tipo de cenário de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="040b2-109">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="040b2-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="040b2-110">Resolution</span></span>  
 <span data-ttu-id="040b2-111">Você pode determinar o local em que a reflexão está sendo usada em seu programa habilitando esse MDA e, em seguida, executando o código em um depurador ou anexando com um depurador quando o MDA é ativado.</span><span class="sxs-lookup"><span data-stu-id="040b2-111">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="040b2-112">Em um depurador, você obterá um rastreamento de pilha mostrando o local em que o cache <xref:System.Reflection.MemberInfo> foi criado e, desse ponto em diante, você poderá determinar o local em que o programa está usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="040b2-112">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="040b2-113">A resolução depende dos objetivos do código.</span><span class="sxs-lookup"><span data-stu-id="040b2-113">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="040b2-114">Esse MDA alerta você de que o programa tem um cenário de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="040b2-114">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="040b2-115">Você talvez queira determinar se você pode substituir um cenário de associação precoce ou considerar o desempenho do cenário de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="040b2-115">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="040b2-116">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="040b2-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="040b2-117">Esse MDA é ativado para cada cache <xref:System.Reflection.MemberInfo> criado.</span><span class="sxs-lookup"><span data-stu-id="040b2-117">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="040b2-118">O impacto de desempenho é negligenciável.</span><span class="sxs-lookup"><span data-stu-id="040b2-118">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="040b2-119">Saída</span><span class="sxs-lookup"><span data-stu-id="040b2-119">Output</span></span>  
 <span data-ttu-id="040b2-120">O MDA gera uma mensagem indicando que o cache <xref:System.Reflection.MemberInfo> foi criado.</span><span class="sxs-lookup"><span data-stu-id="040b2-120">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="040b2-121">Use um depurador para obter um rastreamento de pilha mostrando o local em que o programa está usando reflexão.</span><span class="sxs-lookup"><span data-stu-id="040b2-121">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="040b2-122">Configuração</span><span class="sxs-lookup"><span data-stu-id="040b2-122">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="040b2-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="040b2-123">Example</span></span>  
 <span data-ttu-id="040b2-124">Esse código de exemplo ativará o MDA `memberInfoCacheCreation`.</span><span class="sxs-lookup"><span data-stu-id="040b2-124">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="040b2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="040b2-125">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="040b2-126">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="040b2-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)

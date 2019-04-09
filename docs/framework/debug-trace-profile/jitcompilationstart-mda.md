---
title: MDA jitCompilationStart
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62064286fecc4736f39ad790f0fd7f0e6d84b149
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162339"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="38f2f-102">MDA jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="38f2f-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="38f2f-103">O MDA (Assistente de Depuração Gerenciado) de `jitCompilationStart` é ativado para relatar quando o compilador JIT (Just-In-Time) começa a compilar uma função.</span><span class="sxs-lookup"><span data-stu-id="38f2f-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="38f2f-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="38f2f-104">Symptoms</span></span>  
 <span data-ttu-id="38f2f-105">O tamanho do conjunto de trabalho aumenta para um programa que já está no formato de imagem nativo porque mscorjit é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="38f2f-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="38f2f-106">Causa</span><span class="sxs-lookup"><span data-stu-id="38f2f-106">Cause</span></span>  
 <span data-ttu-id="38f2f-107">Nem todos os assemblies dos quais o programa depende foram gerados em formato nativo ou aqueles que foram não tiveram seu registro feito corretamente.</span><span class="sxs-lookup"><span data-stu-id="38f2f-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="38f2f-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="38f2f-108">Resolution</span></span>  
 <span data-ttu-id="38f2f-109">Habilitar esse MDA permite que você determine qual função está sendo compilada via JIT.</span><span class="sxs-lookup"><span data-stu-id="38f2f-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="38f2f-110">Determine se o assembly que contém a função é gerado no formato nativo e registrado corretamente.</span><span class="sxs-lookup"><span data-stu-id="38f2f-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="38f2f-111">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="38f2f-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="38f2f-112">Esse MDA registra uma mensagem logo antes de um método ser compilado via JIT, então habilitar esse MDA tem um impacto significativo no desempenho.</span><span class="sxs-lookup"><span data-stu-id="38f2f-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="38f2f-113">Observe que, se um método é embutido, esse MDA não gerará uma mensagem separada.</span><span class="sxs-lookup"><span data-stu-id="38f2f-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="38f2f-114">Saída</span><span class="sxs-lookup"><span data-stu-id="38f2f-114">Output</span></span>  
 <span data-ttu-id="38f2f-115">O exemplo de código a seguir mostra uma saída de exemplo.</span><span class="sxs-lookup"><span data-stu-id="38f2f-115">The following code sample shows sample output.</span></span> <span data-ttu-id="38f2f-116">Nesse caso, a saída mostra que, no teste de assembly, o método "m" na classe "ns2.CO" foi compilado via JIT.</span><span class="sxs-lookup"><span data-stu-id="38f2f-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="38f2f-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="38f2f-117">Configuration</span></span>  
 <span data-ttu-id="38f2f-118">O arquivo de configuração a seguir mostra uma variedade de filtros que podem ser utilizados para filtrar quais métodos são relatados quando eles são compilados via JIT pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="38f2f-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="38f2f-119">Você pode especificar que todos os métodos sejam relatados, definindo o valor do atributo name para \*.</span><span class="sxs-lookup"><span data-stu-id="38f2f-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="38f2f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38f2f-120">Example</span></span>  
 <span data-ttu-id="38f2f-121">O exemplo de código a seguir destina-se a ser usado com o arquivo de configuração anterior.</span><span class="sxs-lookup"><span data-stu-id="38f2f-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```csharp
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="38f2f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38f2f-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="38f2f-123">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="38f2f-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="38f2f-124">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="38f2f-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

---
title: MDA (Assistente de depuração gerenciada) jitCompilationStart
description: O MDA (Assistente de depuração gerenciada) jitCompilationStart relata quando o compilador JIT (just-in-time) começa a compilar uma função do .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 13e20c1a940b7bfa777245ba35f3cc1b003d15b2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325526"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="05214-103">MDA jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="05214-103">jitCompilationStart MDA</span></span>

<span data-ttu-id="05214-104">O MDA (Assistente de Depuração Gerenciado) de `jitCompilationStart` é ativado para relatar quando o compilador JIT (Just-In-Time) começa a compilar uma função.</span><span class="sxs-lookup"><span data-stu-id="05214-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="05214-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="05214-105">Symptoms</span></span>  
 <span data-ttu-id="05214-106">O tamanho do conjunto de trabalho aumenta para um programa que já está no formato de imagem nativa, porque mscorjit.dll é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="05214-106">The working set size increases for a program that's already in native image format, because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="05214-107">Causa</span><span class="sxs-lookup"><span data-stu-id="05214-107">Cause</span></span>  
<span data-ttu-id="05214-108">Nem todos os assemblies dos quais o programa depende foram gerados no formato nativo ou um assembly não está registrado corretamente.</span><span class="sxs-lookup"><span data-stu-id="05214-108">Not all the assemblies the program depends on have been generated into native format, or an assembly is not registered correctly.</span></span>  

## <a name="resolution"></a><span data-ttu-id="05214-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="05214-109">Resolution</span></span>  
 <span data-ttu-id="05214-110">Habilitar este MDA permite que você identifique qual função está sendo compilada por JIT.</span><span class="sxs-lookup"><span data-stu-id="05214-110">Enabling this MDA allows you to identify which function is being JIT-compiled.</span></span> <span data-ttu-id="05214-111">Certifique-se de que o assembly que contém a função é gerado para o formato nativo e corretamente registrado.</span><span class="sxs-lookup"><span data-stu-id="05214-111">Make sure that the assembly that contains the function is generated to native format and properly registered.</span></span>
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="05214-112">Efeito no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="05214-112">Effect on the runtime</span></span>  
 <span data-ttu-id="05214-113">Esse MDA registra uma mensagem logo antes de um método ser compilado via JIT, então habilitar esse MDA tem um impacto significativo no desempenho.</span><span class="sxs-lookup"><span data-stu-id="05214-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="05214-114">Se um método estiver embutido, esse MDA não irá gerar uma mensagem separada.</span><span class="sxs-lookup"><span data-stu-id="05214-114">If a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="05214-115">Saída</span><span class="sxs-lookup"><span data-stu-id="05214-115">Output</span></span>  
 <span data-ttu-id="05214-116">O exemplo de código a seguir mostra uma saída de exemplo.</span><span class="sxs-lookup"><span data-stu-id="05214-116">The following code sample shows sample output.</span></span> <span data-ttu-id="05214-117">Nesse caso, a saída mostra que, no teste de assembly, o método "m" na classe "ns2.CO" foi compilado por JIT.</span><span class="sxs-lookup"><span data-stu-id="05214-117">In this case, the output shows that, in assembly Test, the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="05214-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="05214-118">Configuration</span></span>  
 <span data-ttu-id="05214-119">O arquivo de configuração a seguir mostra uma variedade de filtros que podem ser utilizados para filtrar quais métodos são relatados quando eles são compilados via JIT pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="05214-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="05214-120">Você pode especificar que todos os métodos sejam relatados definindo o valor do atributo Name como \* .</span><span class="sxs-lookup"><span data-stu-id="05214-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="05214-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05214-121">Example</span></span>  
 <span data-ttu-id="05214-122">O exemplo de código a seguir destina-se a ser usado com o arquivo de configuração anterior.</span><span class="sxs-lookup"><span data-stu-id="05214-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05214-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="05214-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="05214-124">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="05214-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="05214-125">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="05214-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)

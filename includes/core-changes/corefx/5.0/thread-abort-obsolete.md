---
ms.openlocfilehash: ee67b32b093ebd42f8ac685b34b12f2f6833be86
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332907"
---
### <a name="threadabort-is-obsolete"></a><span data-ttu-id="517a7-101">Thread. Abort é obsoleto</span><span class="sxs-lookup"><span data-stu-id="517a7-101">Thread.Abort is obsolete</span></span>

<span data-ttu-id="517a7-102">As <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs estão obsoletas.</span><span class="sxs-lookup"><span data-stu-id="517a7-102">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="517a7-103">Os projetos que se destinam ao .NET 5,0 ou uma versão posterior encontrarão um aviso de tempo de compilação `SYSLIB0006` se esses métodos forem chamados.</span><span class="sxs-lookup"><span data-stu-id="517a7-103">Projects that target .NET 5.0 or a later version will encounter compile-time warning `SYSLIB0006` if these methods are called.</span></span>

#### <a name="change-description"></a><span data-ttu-id="517a7-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="517a7-104">Change description</span></span>

<span data-ttu-id="517a7-105">Anteriormente, as chamadas para <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> não produziram avisos de tempo de compilação, no entanto, o método lançou um <xref:System.PlatformNotSupportedException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="517a7-105">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="517a7-106">A partir do .NET 5,0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> é marcado como obsoleto como aviso.</span><span class="sxs-lookup"><span data-stu-id="517a7-106">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="517a7-107">Chamar esse método produz o aviso do compilador `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="517a7-107">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="517a7-108">A implementação do método permanece inalterada e continua lançando um <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="517a7-108">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="517a7-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="517a7-109">Reason for change</span></span>

<span data-ttu-id="517a7-110">Considerando que <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> o sempre lança um <xref:System.PlatformNotSupportedException> em todas as implementações do .net, exceto .NET Framework, <xref:System.ObsoleteAttribute> foi adicionado ao método para chamar a atenção para locais onde ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="517a7-110">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="517a7-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="517a7-111">Version introduced</span></span>

<span data-ttu-id="517a7-112">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="517a7-112">5.0 RC 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="517a7-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="517a7-113">Recommended action</span></span>

- <span data-ttu-id="517a7-114">Use um <xref:System.Threading.CancellationToken> para anular o processamento de uma unidade de trabalho em vez de chamar <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="517a7-114">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="517a7-115">O exemplo a seguir ilustra o uso de <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="517a7-115">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

  ```csharp
  void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
  {
      if (QueryIsMoreWorkPending())
      {
          // If the CancellationToken is marked as "needs to cancel",
          // this will throw the appropriate exception.
          cancellationToken.ThrowIfCancellationRequested();

          WorkItem work = DequeueWorkItem();
          ProcessWorkItem(work);
      }
  }
  ```

  <span data-ttu-id="517a7-116">Para saber mais, confira [Cancelamento em threads gerenciados](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="517a7-116">For more information, see [Cancellation in managed threads](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="517a7-117">Para suprimir o aviso de tempo de compilação, suprime o código de aviso `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="517a7-117">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="517a7-118">O código de aviso é específico para <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> e a supressão dele não elimina outros avisos de obsoletion em seu código.</span><span class="sxs-lookup"><span data-stu-id="517a7-118">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="517a7-119">No entanto, recomendamos que você remova <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> as chamadas para, em vez de suprimir o aviso.</span><span class="sxs-lookup"><span data-stu-id="517a7-119">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="517a7-120">Você também pode suprimir o aviso no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="517a7-120">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="517a7-121">Categoria</span><span class="sxs-lookup"><span data-stu-id="517a7-121">Category</span></span>

- <span data-ttu-id="517a7-122">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="517a7-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="517a7-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="517a7-123">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->

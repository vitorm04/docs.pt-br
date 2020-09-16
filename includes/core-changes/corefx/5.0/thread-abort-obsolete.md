---
ms.openlocfilehash: 85488de561a2298f2ff4009ec78b9a6e294053f3
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598171"
---
### <a name="threadabort-is-obsolete"></a><span data-ttu-id="8c694-101">Thread. Abort é obsoleto</span><span class="sxs-lookup"><span data-stu-id="8c694-101">Thread.Abort is obsolete</span></span>

<span data-ttu-id="8c694-102">As <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs estão obsoletas.</span><span class="sxs-lookup"><span data-stu-id="8c694-102">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="8c694-103">Os projetos direcionados ao .NET 5,0 ou uma versão posterior encontrarão avisos de tempo de compilação se esses métodos forem chamados.</span><span class="sxs-lookup"><span data-stu-id="8c694-103">Projects that target .NET 5.0 or a later version will encounter compile-time warnings if these methods are called.</span></span> <span data-ttu-id="8c694-104">Se você suprimir os avisos, um <xref:System.PlatformNotSupportedException> será lançado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8c694-104">If you suppress the warnings, a <xref:System.PlatformNotSupportedException> will be thrown at run time.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8c694-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="8c694-105">Change description</span></span>

<span data-ttu-id="8c694-106">Anteriormente, as chamadas para <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> não produziram avisos de tempo de compilação, no entanto, o método lançou um <xref:System.PlatformNotSupportedException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8c694-106">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="8c694-107">A partir do .NET 5,0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> é marcado como obsoleto como aviso.</span><span class="sxs-lookup"><span data-stu-id="8c694-107">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="8c694-108">Chamar esse método produz o aviso do compilador `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="8c694-108">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="8c694-109">A implementação do método permanece inalterada e continua lançando um <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="8c694-109">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8c694-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="8c694-110">Reason for change</span></span>

<span data-ttu-id="8c694-111">Considerando que <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> o sempre lança um <xref:System.PlatformNotSupportedException> em todas as implementações do .net, exceto .NET Framework, <xref:System.ObsoleteAttribute> foi adicionado ao método para chamar a atenção para locais onde ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="8c694-111">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8c694-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8c694-112">Version introduced</span></span>

<span data-ttu-id="8c694-113">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="8c694-113">5.0 RC 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c694-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8c694-114">Recommended action</span></span>

- <span data-ttu-id="8c694-115">Use um <xref:System.Threading.CancellationToken> para anular o processamento de uma unidade de trabalho em vez de chamar <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8c694-115">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8c694-116">O exemplo a seguir ilustra o uso de <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="8c694-116">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

  <span data-ttu-id="8c694-117">Para saber mais, confira [Cancelamento em threads gerenciados](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="8c694-117">For more information, see [Cancellation in managed threads](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="8c694-118">Para suprimir o aviso de tempo de compilação, suprime o código de aviso `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="8c694-118">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="8c694-119">O código de aviso é específico para <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> e a supressão dele não elimina outros avisos de obsoletion em seu código.</span><span class="sxs-lookup"><span data-stu-id="8c694-119">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="8c694-120">No entanto, recomendamos que você remova <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> as chamadas para, em vez de suprimir o aviso.</span><span class="sxs-lookup"><span data-stu-id="8c694-120">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="8c694-121">Você também pode suprimir o aviso no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="8c694-121">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="8c694-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="8c694-122">Category</span></span>

- <span data-ttu-id="8c694-123">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="8c694-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c694-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8c694-124">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->

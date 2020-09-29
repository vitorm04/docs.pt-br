---
ms.openlocfilehash: 8693c1fdef5fa194b16127d4f1dd87e23ad68f2d
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438034"
---
### <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a><span data-ttu-id="dfcd9-101">A conversão de RCW em uma `InterfaceIsIInspectable` interface gera PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="dfcd9-101">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>

<span data-ttu-id="dfcd9-102">A conversão de um RCW (Runtime Callable Wrapper) em uma interface marcada como <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> agora gera um <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="dfcd9-102">Casting a runtime callable wrapper (RCW) to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> now throws a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="dfcd9-103">Essa alteração é um acompanhamento da [remoção do suporte do WinRT do .net](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span><span class="sxs-lookup"><span data-stu-id="dfcd9-103">This change is a follow up to the [removal of WinRT support from .NET](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dfcd9-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dfcd9-104">Version introduced</span></span>

<span data-ttu-id="dfcd9-105">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="dfcd9-105">5.0 RC2</span></span>

#### <a name="change-description"></a><span data-ttu-id="dfcd9-106">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="dfcd9-106">Change description</span></span>

<span data-ttu-id="dfcd9-107">Em versões do .NET anteriores ao .NET 5,0 Preview 6, a conversão de um RCW em uma interface marcada como <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> funciona conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-107">In .NET versions prior to .NET 5.0 preview 6, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> works as expected.</span></span> <span data-ttu-id="dfcd9-108">Nas visualizações do .NET 5,0 6-8 e RC1, você pode converter com êxito um RCW em uma <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-108">In .NET 5.0 previews 6-8 and RC1, you can successfully cast an RCW to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span></span> <span data-ttu-id="dfcd9-109">No entanto, você pode obter violações de acesso ao executar métodos na interface, porque o suporte subjacente no tempo de execução [foi removido no .net 5,0 Preview 6](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span><span class="sxs-lookup"><span data-stu-id="dfcd9-109">However, you might get access violations when you execute methods on the interface, because the underlying support in the runtime [was removed in .NET 5.0 preview 6](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span>

<span data-ttu-id="dfcd9-110">No .NET 5,0 RC2 e versões posteriores, converter um RCW em uma interface marcada como <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> lança um <xref:System.PlatformNotSupportedException> no momento da conversão.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-110">In .NET 5.0 RC2 and later versions, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> throws a <xref:System.PlatformNotSupportedException> at cast time.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dfcd9-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="dfcd9-111">Reason for change</span></span>

<span data-ttu-id="dfcd9-112">O suporte para <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> foi [removido em uma versão prévia anterior do .NET 5,0](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span><span class="sxs-lookup"><span data-stu-id="dfcd9-112">The support for <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> was [removed in a previous .NET 5.0 preview](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span> <span data-ttu-id="dfcd9-113">No entanto, a conversão para uma <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface foi acidentalmente ignorada.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-113">However, casting to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface was accidentally overlooked.</span></span> <span data-ttu-id="dfcd9-114">Como o suporte subjacente no tempo de execução não existe mais, lançar um <xref:System.PlatformNotSupportedException> habilita um caminho de falha normal.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-114">Since the underlying support in the runtime no longer exists, throwing a <xref:System.PlatformNotSupportedException> enables a graceful failure path.</span></span> <span data-ttu-id="dfcd9-115">Gerar uma exceção também o torna mais detectável que esse recurso não é mais suportado.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-115">Throwing an exception also makes it more discoverable that this feature is no longer supported.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dfcd9-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="dfcd9-116">Recommended action</span></span>

- <span data-ttu-id="dfcd9-117">Se você puder definir a interface em um arquivo de metadados do tempo de execução do Windows (WinMD), use a ferramenta/WinRT do C# em vez disso.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-117">If you can define the interface in a Windows runtime metadata (WinMD) file, use the C#/WinRT tool instead.</span></span>

- <span data-ttu-id="dfcd9-118">Caso contrário, marque a interface como <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> em vez de <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> e adicione três entradas fictícias ao início da interface para os <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> métodos.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-118">Otherwise, mark the interface as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> instead of <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, and add three dummy entries to the start of the interface for the <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> methods.</span></span> <span data-ttu-id="dfcd9-119">O trecho de código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="dfcd9-119">The following code snippet shows an example.</span></span>

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

#### <a name="category"></a><span data-ttu-id="dfcd9-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="dfcd9-120">Category</span></span>

<span data-ttu-id="dfcd9-121">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="dfcd9-121">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dfcd9-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="dfcd9-122">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

-->

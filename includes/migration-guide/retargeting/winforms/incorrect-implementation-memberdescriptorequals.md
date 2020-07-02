---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614299"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a><span data-ttu-id="63de5-101">Implementação incorreta de MemberDescriptor.Equals</span><span class="sxs-lookup"><span data-stu-id="63de5-101">Incorrect implementation of MemberDescriptor.Equals</span></span>

#### <a name="details"></a><span data-ttu-id="63de5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="63de5-102">Details</span></span>

<span data-ttu-id="63de5-103">A implementação original do método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> compara duas propriedades de cadeia de caracteres diferentes dos objetos que estão sendo comparados: o nome da categoria e a cadeia de caracteres de descrição.</span><span class="sxs-lookup"><span data-stu-id="63de5-103">The original implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method compares two different string properties from the objects being compared: the category name and the description string.</span></span> <span data-ttu-id="63de5-104">A correção é para comparar o <xref:System.ComponentModel.MemberDescriptor.Category> do primeiro objeto com o <xref:System.ComponentModel.MemberDescriptor.Category> de um segundo objeto, e o <xref:System.ComponentModel.MemberDescriptor.Description> do primeiro com o <xref:System.ComponentModel.MemberDescriptor.Description> do segunda.</span><span class="sxs-lookup"><span data-stu-id="63de5-104">The fix is to compare the <xref:System.ComponentModel.MemberDescriptor.Category> of the first object to the <xref:System.ComponentModel.MemberDescriptor.Category> of the second one, and the <xref:System.ComponentModel.MemberDescriptor.Description> of the first to the <xref:System.ComponentModel.MemberDescriptor.Description> of the second.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="63de5-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="63de5-105">Suggestion</span></span>

<span data-ttu-id="63de5-106">Se seu aplicativo depende do <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> e, às vezes, retorna `false` quando os descritores são equivalentes, e você está direcionado ao .NET Framework 4.6.2 ou posterior, há várias opções:</span><span class="sxs-lookup"><span data-stu-id="63de5-106">If your application depends on <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> sometimes returning `false` when descriptors are equivalent, and you are targeting the .NET Framework 4.6.2 or later, you have several options:</span></span>

- <span data-ttu-id="63de5-107">Fazer alterações no código para comparar os campos <xref:System.ComponentModel.MemberDescriptor.Category> e <xref:System.ComponentModel.MemberDescriptor.Description> manualmente além de chamar o método <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63de5-107">Make code changes to compare the <xref:System.ComponentModel.MemberDescriptor.Category> and <xref:System.ComponentModel.MemberDescriptor.Description> fields manually in addition to calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="63de5-108">Recuse essa alteração adicionando o seguinte valor ao arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="63de5-108">Opt out of this change by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

<span data-ttu-id="63de5-109">Se seu aplicativo for direcionado ao NET Framework 4.6.1 ou anterior e executado no .NET Framework 4.6.2 ou posterior e você quiser que essa alteração seja habilitada, defina a opção de compatibilidade como `false` adicionando o seguinte valor ao arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="63de5-109">If your application targets .NET Framework 4.6.1 or earlier and is running on the .NET Framework 4.6.2 or later and you want this change enabled, you can set the compatibility switch to `false` by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| <span data-ttu-id="63de5-110">Name</span><span class="sxs-lookup"><span data-stu-id="63de5-110">Name</span></span>    | <span data-ttu-id="63de5-111">Valor</span><span class="sxs-lookup"><span data-stu-id="63de5-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="63de5-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="63de5-112">Scope</span></span>   | <span data-ttu-id="63de5-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="63de5-113">Edge</span></span>        |
| <span data-ttu-id="63de5-114">Versão</span><span class="sxs-lookup"><span data-stu-id="63de5-114">Version</span></span> | <span data-ttu-id="63de5-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="63de5-115">4.6.2</span></span>       |
| <span data-ttu-id="63de5-116">Type</span><span class="sxs-lookup"><span data-stu-id="63de5-116">Type</span></span>    | <span data-ttu-id="63de5-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="63de5-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="63de5-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="63de5-118">Affected APIs</span></span>

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>

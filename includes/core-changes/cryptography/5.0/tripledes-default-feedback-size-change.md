---
ms.openlocfilehash: 2599e1f65720c25695f1fb5cfa39cabb842efc1d
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888602"
---
### <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a><span data-ttu-id="79e0b-101">Valor de FeedbackSize padrão para instâncias criadas por TripleDES. Create alterado</span><span class="sxs-lookup"><span data-stu-id="79e0b-101">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>

<span data-ttu-id="79e0b-102">O valor padrão da <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> Propriedade na <xref:System.Security.Cryptography.TripleDES> instância retornada de <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> foi alterado de 64 para 8 para tornar a migração de .NET Framework mais fácil.</span><span class="sxs-lookup"><span data-stu-id="79e0b-102">The default value for the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> property on the <xref:System.Security.Cryptography.TripleDES> instance returned from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> has changed from 64 to 8 to make migration from .NET Framework easier.</span></span> <span data-ttu-id="79e0b-103">Essa propriedade, a menos que usada diretamente no código do chamador, é usada somente quando a <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> propriedade é <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="79e0b-103">This property, unless used directly in caller code, is used only when the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property is <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="79e0b-104">O suporte para o <xref:System.Security.Cryptography.CipherMode.CFB> modo foi adicionado primeiro ao .net para a versão 5,0 RC1, portanto, somente os aplicativos .net 5,0 RC1 e .net 5,0 RC2 devem ser afetados por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="79e0b-104">Support for the <xref:System.Security.Cryptography.CipherMode.CFB> mode was first added to .NET for the 5.0 RC1 release, so only .NET 5.0 RC1 and .NET 5.0 RC2 applications should be impacted by this change.</span></span>

#### <a name="change-description"></a><span data-ttu-id="79e0b-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="79e0b-105">Change description</span></span>

<span data-ttu-id="79e0b-106">No .NET Core e nas versões anteriores de pré-lançamento do .NET 5,0, `TripleDES.Create().FeedbackSize` o tem um valor padrão de 64.</span><span class="sxs-lookup"><span data-stu-id="79e0b-106">In .NET Core and previous pre-release versions of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 64.</span></span> <span data-ttu-id="79e0b-107">A partir da versão RTM do .NET 5,0, `TripleDES.Create().FeedbackSize` tem um valor padrão de 8.</span><span class="sxs-lookup"><span data-stu-id="79e0b-107">Starting in the RTM version of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 8.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="79e0b-108">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="79e0b-108">Reason for change</span></span>

<span data-ttu-id="79e0b-109">Em .NET Framework, a <xref:System.Security.Cryptography.TripleDES> classe base usa como padrão o valor de <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 64, mas a <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> classe substitui o padrão por 8.</span><span class="sxs-lookup"><span data-stu-id="79e0b-109">In .NET Framework, the <xref:System.Security.Cryptography.TripleDES> base class defaults the value of <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> to 64, but the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class overwrites the default to 8.</span></span> <span data-ttu-id="79e0b-110">Quando a <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriedade foi introduzida no .NET Core na versão 2,0, esse mesmo comportamento foi preservado.</span><span class="sxs-lookup"><span data-stu-id="79e0b-110">When the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property was introduced to .NET Core in version 2.0, this same behavior was preserved.</span></span> <span data-ttu-id="79e0b-111">No entanto, em .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> retorna uma instância do <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> , portanto, o valor padrão da fábrica de algoritmos é 8.</span><span class="sxs-lookup"><span data-stu-id="79e0b-111">However, in .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> returns an instance of <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, so the default value from the algorithm factory is 8.</span></span> <span data-ttu-id="79e0b-112">Para .NET Core e .NET 5 +, a fábrica de algoritmos retorna uma implementação não pública, que, até agora, tinha um valor padrão de 64.</span><span class="sxs-lookup"><span data-stu-id="79e0b-112">For .NET Core and .NET 5+, the algorithm factory returns a non-public implementation, which, until now, had a default value of 64.</span></span>

<span data-ttu-id="79e0b-113">A alteração da <xref:System.Security.Cryptography.TripleDES> classe de implementação ' o <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> valor para 8 permite que aplicativos escritos para .NET Framework que especificam o modo de codificação como <xref:System.Security.Cryptography.CipherMode.CFB> , mas que não tenham sido explicitamente atribuídos à <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriedade, continuem a funcionar no .NET 5.</span><span class="sxs-lookup"><span data-stu-id="79e0b-113">Changing the <xref:System.Security.Cryptography.TripleDES> implementation class' <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> value to 8 allows for applications written for .NET Framework that specified the cipher mode as <xref:System.Security.Cryptography.CipherMode.CFB> but didn't explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property, to continue to function on .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="79e0b-114">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="79e0b-114">Version introduced</span></span>

<span data-ttu-id="79e0b-115">5,0 RTM</span><span class="sxs-lookup"><span data-stu-id="79e0b-115">5.0 RTM</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="79e0b-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="79e0b-116">Recommended action</span></span>

<span data-ttu-id="79e0b-117">Os aplicativos que criptografam ou descriptografam dados nas versões RC1 ou RC2 do .NET 5,0 fazem isso com o CFB64, quando as seguintes condições são atendidas:</span><span class="sxs-lookup"><span data-stu-id="79e0b-117">Applications that encrypt or decrypt data in the RC1 or RC2 versions of .NET 5.0 do so with CFB64, when the following conditions are met:</span></span>

- <span data-ttu-id="79e0b-118">Com uma <xref:System.Security.Cryptography.TripleDES> instância do <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="79e0b-118">With a <xref:System.Security.Cryptography.TripleDES> instance from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="79e0b-119">Usando o valor padrão para <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .</span><span class="sxs-lookup"><span data-stu-id="79e0b-119">Using the default value for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span>
- <span data-ttu-id="79e0b-120">Com a <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> propriedade definida como <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="79e0b-120">With the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property set to <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="79e0b-121">Para manter esse comportamento, atribua a <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> Propriedade a `64` .</span><span class="sxs-lookup"><span data-stu-id="79e0b-121">To maintain this behavior, assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property to `64`.</span></span>

<span data-ttu-id="79e0b-122">Nem todas as `TripleDES` implementações usam o mesmo padrão para <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .</span><span class="sxs-lookup"><span data-stu-id="79e0b-122">Not all `TripleDES` implementations use the same default for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span> <span data-ttu-id="79e0b-123">Recomendamos que, se você usar o <xref:System.Security.Cryptography.CipherMode.CFB> modo de codificação em <xref:System.Security.Cryptography.TripleDES> instâncias, deverá sempre atribuir explicitamente o <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="79e0b-123">We recommend that if you use the <xref:System.Security.Cryptography.CipherMode.CFB> cipher mode on <xref:System.Security.Cryptography.TripleDES> instances, you should always explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property value.</span></span>

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

#### <a name="category"></a><span data-ttu-id="79e0b-124">Categoria</span><span class="sxs-lookup"><span data-stu-id="79e0b-124">Category</span></span>

- <span data-ttu-id="79e0b-125">Criptografia</span><span class="sxs-lookup"><span data-stu-id="79e0b-125">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="79e0b-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="79e0b-126">Affected APIs</span></span>

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

-->

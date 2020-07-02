---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614273"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a><span data-ttu-id="cd491-101">Descriptografador AesCryptoServiceProvider fornece uma transformação reutilizável</span><span class="sxs-lookup"><span data-stu-id="cd491-101">AesCryptoServiceProvider decryptor provides a reusable transform</span></span>

#### <a name="details"></a><span data-ttu-id="cd491-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="cd491-102">Details</span></span>

<span data-ttu-id="cd491-103">Começando com aplicativos destinados ao .NET Framework 4.6.2, o descriptografador <xref:System.Security.Cryptography.AesCryptoServiceProvider> fornece uma transformação reutilizável.</span><span class="sxs-lookup"><span data-stu-id="cd491-103">Starting with apps that target the .NET Framework 4.6.2, the <xref:System.Security.Cryptography.AesCryptoServiceProvider> decryptor provides a reusable transform.</span></span> <span data-ttu-id="cd491-104">Após uma chamada para <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, a transformação é reinicializada e pode ser reutilizada.</span><span class="sxs-lookup"><span data-stu-id="cd491-104">After a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, the transform is reinitialized and can be reused.</span></span> <span data-ttu-id="cd491-105">Para aplicativos destinados a versões anteriores do .NET Framework, tentar reutilizar o descriptografador chamando <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> após uma chamada para <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> gera um <xref:System.Security.Cryptography.CryptographicException> ou produz dados corrompidos.</span><span class="sxs-lookup"><span data-stu-id="cd491-105">For apps that target earlier versions of the .NET Framework, attempting to reuse the decryptor by calling <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> after a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> throws a <xref:System.Security.Cryptography.CryptographicException> or produces corrupted data.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cd491-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="cd491-106">Suggestion</span></span>

<span data-ttu-id="cd491-107">O impacto dessa alteração deve ser mínimo, uma vez que se trata do comportamento esperado. Aplicativos que dependem do comportamento anterior podem optar por não usá-lo adicionando a seguinte definição de configuração à seção `<runtime>` do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="cd491-107">The impact of this change should be minimal, since this is the expected behavior.Applications that depend on the previous behavior can opt out of it using it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

<span data-ttu-id="cd491-108">Além disso, aplicativos destinados a uma versão anterior do .NET Framework, mas em execução em uma versão do .NET Framework a partir do .NET Framework 4.6.2 podem aceitá-lo adicionando a seguinte definição de configuração à seção `<runtime>` do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="cd491-108">In addition, applications that target a previous version of the .NET Framework but are running under a version of the .NET Framework starting with .NET Framework 4.6.2 can opt in to it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| <span data-ttu-id="cd491-109">Name</span><span class="sxs-lookup"><span data-stu-id="cd491-109">Name</span></span>    | <span data-ttu-id="cd491-110">Valor</span><span class="sxs-lookup"><span data-stu-id="cd491-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cd491-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="cd491-111">Scope</span></span>   | <span data-ttu-id="cd491-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="cd491-112">Minor</span></span>       |
| <span data-ttu-id="cd491-113">Versão</span><span class="sxs-lookup"><span data-stu-id="cd491-113">Version</span></span> | <span data-ttu-id="cd491-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="cd491-114">4.6.2</span></span>       |
| <span data-ttu-id="cd491-115">Type</span><span class="sxs-lookup"><span data-stu-id="cd491-115">Type</span></span>    | <span data-ttu-id="cd491-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="cd491-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cd491-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="cd491-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>

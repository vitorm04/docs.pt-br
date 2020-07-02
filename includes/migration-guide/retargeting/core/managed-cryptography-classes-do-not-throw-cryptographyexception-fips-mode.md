---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617777"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a><span data-ttu-id="604ce-101">Classes de criptografia gerenciadas não geram uma CryptographyException no modo FIPS</span><span class="sxs-lookup"><span data-stu-id="604ce-101">Managed cryptography classes do not throw a CryptographyException in FIPS mode</span></span>

#### <a name="details"></a><span data-ttu-id="604ce-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="604ce-102">Details</span></span>

<span data-ttu-id="604ce-103">No .NET Framework 4.7.2 e em versões anteriores, as classes de provedor criptográfico gerenciadas, como <xref:System.Security.Cryptography.SHA256Managed>, geram uma <xref:System.Security.Cryptography.CryptographicException> quando as bibliotecas criptográficas do sistema estão configuradas no modo FIPS.</span><span class="sxs-lookup"><span data-stu-id="604ce-103">In .NET Framework 4.7.2 and earlier versions, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in FIPS mode.</span></span> <span data-ttu-id="604ce-104">Essas exceções são geradas porque as versões gerenciadas não foram submetidas à certificação 140-2 do padrão FIPS para bloquear algoritmos criptográficos que não foram considerados aprovados com base nas regras do FIPS.</span><span class="sxs-lookup"><span data-stu-id="604ce-104">These exceptions are thrown because the managed versions have not undergone FIPS (Federal Information Processing Standards) 140-2 certification, as well as to block cryptographic algorithms that were not considered to be approved based on the FIPS rules.</span></span>  <span data-ttu-id="604ce-105">Como poucos desenvolvedores têm computadores de desenvolvimento no modo FIPS, essas exceções são frequentemente geradas apenas em sistemas de produção. Aplicativos que direcionam o .NET Framework 4.8 e versões posteriores mudam automaticamente para a política flexibilizada mais recente para que um <xref:System.Security.Cryptography.CryptographicException> não seja mais gerado por padrão nesses casos.</span><span class="sxs-lookup"><span data-stu-id="604ce-105">Because few developers have their development machines in FIPS mode, these exceptions are frequently thrown only on production systems.Applications that target .NET Framework 4.8 and later versions automatically switch to the newer, relaxed policy, so that a <xref:System.Security.Cryptography.CryptographicException> is no longer thrown by default in such cases.</span></span> <span data-ttu-id="604ce-106">Em vez disso, as classes de criptografia gerenciadas redirecionam as operações criptográficas para uma biblioteca de criptografia do sistema.</span><span class="sxs-lookup"><span data-stu-id="604ce-106">Instead, the managed cryptography classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="604ce-107">Essa alteração na política elimina efetivamente uma diferença potencialmente confusa entre os ambientes do desenvolvedor e os ambientes de produção, fazendo com que componentes nativos e componentes gerenciados operem sob a mesma política criptográfica.</span><span class="sxs-lookup"><span data-stu-id="604ce-107">This policy change effectively removes a potentially confusing difference between developer environments and the production environments and makes native components and managed components operate under the same cryptographic policy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="604ce-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="604ce-108">Suggestion</span></span>

<span data-ttu-id="604ce-109">Se esse comportamento for indesejável, será possível recusá-lo e restaurar o anterior para que um <xref:System.Security.Cryptography.CryptographicException> seja gerado em modo FIPS adicionando a configuração a seguir [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="604ce-109">If this behavior is undesirable, you can opt out of it and restore the previous behavior so that a <xref:System.Security.Cryptography.CryptographicException> is thrown in FIPS mode by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

<span data-ttu-id="604ce-110">Se seu aplicativo direcionar o .NET Framework 4.7.2 ou versões anteriores, também será possível aceitar essa alteração adicionando a seguinte configuração [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="604ce-110">If your application targets .NET Framework 4.7.2 or earlier, you can also opt in to this change by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| <span data-ttu-id="604ce-111">Name</span><span class="sxs-lookup"><span data-stu-id="604ce-111">Name</span></span>    | <span data-ttu-id="604ce-112">Valor</span><span class="sxs-lookup"><span data-stu-id="604ce-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="604ce-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="604ce-113">Scope</span></span>   | <span data-ttu-id="604ce-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="604ce-114">Edge</span></span>        |
| <span data-ttu-id="604ce-115">Versão</span><span class="sxs-lookup"><span data-stu-id="604ce-115">Version</span></span> | <span data-ttu-id="604ce-116">4.8</span><span class="sxs-lookup"><span data-stu-id="604ce-116">4.8</span></span>         |
| <span data-ttu-id="604ce-117">Type</span><span class="sxs-lookup"><span data-stu-id="604ce-117">Type</span></span>    | <span data-ttu-id="604ce-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="604ce-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="604ce-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="604ce-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>

---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568003"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="46f1d-101">EnvelopedCms é padrão para criptografia AES-256</span><span class="sxs-lookup"><span data-stu-id="46f1d-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="46f1d-102">O algoritmo de criptografia simétrico padrão usado por `EnvelopedCms` foi alterado de TripleDES para AES-256.</span><span class="sxs-lookup"><span data-stu-id="46f1d-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="46f1d-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="46f1d-103">Change description</span></span>

<span data-ttu-id="46f1d-104">Em versões do .NET <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> Core Preview 7 e anteriores, quando são usadas para criptografar dados sem especificar um algoritmo de criptografia simétrica através de uma sobrecarga de construtor, os dados foram criptografados com o algoritmo TripleDES/3DES/3DEA/DES3-EDE.</span><span class="sxs-lookup"><span data-stu-id="46f1d-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="46f1d-105">Começando com o pacote .NET Core 3.0 Preview 8 (via versão 4.6.0 do [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet), o algoritmo padrão foi alterado para AES-256 para modernização de algoritmos e para melhorar a segurança das opções padrão.</span><span class="sxs-lookup"><span data-stu-id="46f1d-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="46f1d-106">Se um certificado de destinatário de mensagens tiver uma chave pública Diffie-Hellman <xref:System.Security.Cryptography.CryptographicException> (não CE), a operação de criptografia pode falhar devido a limitações na plataforma subjacente.</span><span class="sxs-lookup"><span data-stu-id="46f1d-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="46f1d-107">No código de amostra a seguir, os dados são criptografados com O TriploDES se estiver em execução no .NET Core 3.0 Preview 7 ou anterior.</span><span class="sxs-lookup"><span data-stu-id="46f1d-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="46f1d-108">Se estiver sendo executado no .NET Core 3.0 Preview 8 ou posterior, ele será criptografado com a AES-256.</span><span class="sxs-lookup"><span data-stu-id="46f1d-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="46f1d-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="46f1d-109">Version introduced</span></span>

<span data-ttu-id="46f1d-110">3.0 Visualização 8</span><span class="sxs-lookup"><span data-stu-id="46f1d-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="46f1d-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="46f1d-111">Recommended action</span></span>

<span data-ttu-id="46f1d-112">Se você for impactado negativamente pela alteração, você pode restaurar a criptografia TripleDES <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> especificando explicitamente o identificador <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>de algoritmo de criptografia em um construtor que inclui um parâmetro de tipo, como:</span><span class="sxs-lookup"><span data-stu-id="46f1d-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="46f1d-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="46f1d-113">Category</span></span>

<span data-ttu-id="46f1d-114">Criptografia</span><span class="sxs-lookup"><span data-stu-id="46f1d-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="46f1d-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="46f1d-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->

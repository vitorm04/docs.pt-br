---
ms.openlocfilehash: e0cdcce9b8c7d591925b08635e3354dadaf22b7b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556015"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="05865-101">EnvelopedCms usa como padrão a criptografia AES-256</span><span class="sxs-lookup"><span data-stu-id="05865-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="05865-102">O algoritmo de criptografia simétrica padrão usado pelo `EnvelopedCms` foi alterado de TripleDES para AES-256.</span><span class="sxs-lookup"><span data-stu-id="05865-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="05865-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="05865-103">Change description</span></span>

<span data-ttu-id="05865-104">Em versões anteriores, quando <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> é usado para criptografar dados sem especificar um algoritmo de criptografia simétrica por meio de uma sobrecarga de construtor, os dados são criptografados com o algoritmo TripleDES/3DES/3DEA/DES3-Ede.</span><span class="sxs-lookup"><span data-stu-id="05865-104">In previous versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data is encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="05865-105">A partir do .NET Core 3,0 (por meio da versão 4.6.0 do pacote NuGet [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ), o algoritmo padrão foi alterado para AES-256 para modernização do algoritmo e para melhorar a segurança das opções padrão.</span><span class="sxs-lookup"><span data-stu-id="05865-105">Starting with .NET Core 3.0 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="05865-106">Se um certificado de destinatário de mensagem tiver uma chave pública Diffie-Hellman (não-EC), a operação de criptografia poderá falhar com um <xref:System.Security.Cryptography.CryptographicException> devido a limitações na plataforma subjacente.</span><span class="sxs-lookup"><span data-stu-id="05865-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="05865-107">No código de exemplo a seguir, os dados são criptografados com TripleDES se executados no .NET Core 2,2 ou anterior.</span><span class="sxs-lookup"><span data-stu-id="05865-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 2.2 or earlier.</span></span> <span data-ttu-id="05865-108">Se estiver executando no .NET Core 3,0 ou posterior, ele será criptografado com AES-256.</span><span class="sxs-lookup"><span data-stu-id="05865-108">If running on .NET Core 3.0 or later, it's encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="05865-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="05865-109">Version introduced</span></span>

<span data-ttu-id="05865-110">3.0</span><span class="sxs-lookup"><span data-stu-id="05865-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="05865-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="05865-111">Recommended action</span></span>

<span data-ttu-id="05865-112">Se você for afetado negativamente pela alteração, poderá restaurar a criptografia TripleDES especificando explicitamente o identificador do algoritmo de criptografia em um <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> Construtor que inclua um parâmetro do tipo <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> , como:</span><span class="sxs-lookup"><span data-stu-id="05865-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="05865-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="05865-113">Category</span></span>

<span data-ttu-id="05865-114">Criptografia</span><span class="sxs-lookup"><span data-stu-id="05865-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="05865-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="05865-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->

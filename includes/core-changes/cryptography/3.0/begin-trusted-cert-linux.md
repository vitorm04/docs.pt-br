---
ms.openlocfilehash: 1d9a5bbea49730ee6cf99eaae6b20a0035e70b97
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135588"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a><span data-ttu-id="740ba-101">Sintaxe "BEGIN TRUSTed CERTIFICATE" não é mais suportada para certificados raiz no Linux</span><span class="sxs-lookup"><span data-stu-id="740ba-101">"BEGIN TRUSTED CERTIFICATE" syntax no longer supported for root certificates on Linux</span></span>

<span data-ttu-id="740ba-102">Os certificados raiz no Linux e em outros sistemas semelhantes a UNIX (mas não macOS) podem ser apresentados em duas formas: `BEGIN CERTIFICATE` o cabeçalho PEM padrão e o cabeçalho PEM `BEGIN TRUSTED CERTIFICATE` específico do OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="740ba-102">Root certificates on Linux and other Unix-like systems (but not macOS) can be presented in two forms: the standard `BEGIN CERTIFICATE` PEM header, and the OpenSSL-specific `BEGIN TRUSTED CERTIFICATE` PEM header.</span></span> <span data-ttu-id="740ba-103">A última sintaxe permite uma configuração adicional que causou problemas de compatibilidade com a classe do <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> .NET Core.</span><span class="sxs-lookup"><span data-stu-id="740ba-103">The latter syntax allows for additional configuration that has caused compatibility issues with .NET Core's <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> class.</span></span> <span data-ttu-id="740ba-104">`BEGIN TRUSTED CERTIFICATE`o conteúdo do certificado raiz não é mais carregado pelo mecanismo de cadeia a partir do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="740ba-104">`BEGIN TRUSTED CERTIFICATE` root certificate contents are no longer loaded by the chain engine starting in .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="740ba-105">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="740ba-105">Change description</span></span>

<span data-ttu-id="740ba-106">Anteriormente, as `BEGIN CERTIFICATE` sintaxes `BEGIN TRUSTED CERTIFICATE` e foram usadas para popular a lista de confiança raiz.</span><span class="sxs-lookup"><span data-stu-id="740ba-106">Previously, both the `BEGIN CERTIFICATE` and `BEGIN TRUSTED CERTIFICATE` syntaxes were used to populate the root trust list.</span></span> <span data-ttu-id="740ba-107">Se a `BEGIN TRUSTED CERTIFICATE` sintaxe tiver sido usada e opções adicionais tiverem sido especificadas no arquivo <xref:System.Security.Cryptography.X509Certificates.X509Chain> , talvez tenha relatado que a confiança da cadeia foi explicitamente despermitida<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>().</span><span class="sxs-lookup"><span data-stu-id="740ba-107">If the `BEGIN TRUSTED CERTIFICATE` syntax was used and additional options were specified in the file, <xref:System.Security.Cryptography.X509Certificates.X509Chain> may have reported that the chain trust was explicitly disallowed (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>).</span></span> <span data-ttu-id="740ba-108">No entanto, se o certificado também tiver sido `BEGIN CERTIFICATE` especificado com a sintaxe em um arquivo carregado anteriormente, a cadeia de confiança era permitida.</span><span class="sxs-lookup"><span data-stu-id="740ba-108">However, if the certificate was also specified with the `BEGIN CERTIFICATE` syntax in a previously loaded file, the chain trust was allowed.</span></span>

<span data-ttu-id="740ba-109">A partir do .NET Core 3,0 `BEGIN TRUSTED CERTIFICATE` , o conteúdo não é mais lido.</span><span class="sxs-lookup"><span data-stu-id="740ba-109">Starting in .NET Core 3.0, `BEGIN TRUSTED CERTIFICATE` contents are no longer read.</span></span> <span data-ttu-id="740ba-110">Se o certificado também não for especificado por meio de `BEGIN CERTIFICATE` uma sintaxe padrão <xref:System.Security.Cryptography.X509Certificates.X509Chain> , os relatórios que a raiz não é<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>confiável ().</span><span class="sxs-lookup"><span data-stu-id="740ba-110">If the certificate is not also specified via a standard `BEGIN CERTIFICATE` syntax, the <xref:System.Security.Cryptography.X509Certificates.X509Chain> reports that the root is not trusted (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="740ba-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="740ba-111">Version introduced</span></span>

<span data-ttu-id="740ba-112">3.0</span><span class="sxs-lookup"><span data-stu-id="740ba-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="740ba-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="740ba-113">Recommended action</span></span>

<span data-ttu-id="740ba-114">A maioria dos aplicativos não é afetada por essa alteração, mas os aplicativos que não podem ver ambas as fontes de certificado raiz devido `UntrustedRoot` a problemas de permissões podem apresentar erros inesperados após a atualização.</span><span class="sxs-lookup"><span data-stu-id="740ba-114">Most applications are unaffected by this change, but applications that cannot see both root certificate sources because of permissions problems may experience unexpected `UntrustedRoot` errors after upgrading.</span></span>

<span data-ttu-id="740ba-115">Muitas distribuições do Linux (ou distribuições) gravam certificados raiz em dois locais: um diretório de um certificado por arquivo e uma concatenação de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="740ba-115">Many Linux distributions (or distros) write root certificates into two locations: a one-certificate-per-file directory, and a one-file concatenation.</span></span> <span data-ttu-id="740ba-116">Em alguns distribuições, o diretório de um certificado por arquivo usa a `BEGIN TRUSTED CERTIFICATE` sintaxe enquanto a concatenação de arquivo usa a sintaxe padrão `BEGIN CERTIFICATE` .</span><span class="sxs-lookup"><span data-stu-id="740ba-116">On some distros, the one-certificate-per-file directory uses the `BEGIN TRUSTED CERTIFICATE` syntax while the file concatenation uses the standard `BEGIN CERTIFICATE` syntax.</span></span> <span data-ttu-id="740ba-117">Certifique-se de que todos os certificados raiz `BEGIN CERTIFICATE` personalizados sejam adicionados como em pelo menos um desses locais e que ambos os locais possam ser lidos pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="740ba-117">Ensure that any custom root certificates are added as `BEGIN CERTIFICATE` in at least one of these locations, and that both locations can be read by your application.</span></span>

<span data-ttu-id="740ba-118">O diretório típico é */etc/SSL/Certs/* e o arquivo concatenado típico é */etc/ssl/cert.pem*.</span><span class="sxs-lookup"><span data-stu-id="740ba-118">The typical directory is */etc/ssl/certs/* and the typical concatenated file is */etc/ssl/cert.pem*.</span></span> <span data-ttu-id="740ba-119">Use o comando `openssl version -d` para determinar a raiz específica da plataforma, que pode ser diferente de */etc/SSL/*.</span><span class="sxs-lookup"><span data-stu-id="740ba-119">Use the command `openssl version -d` to determine the platform-specific root, which may differ from */etc/ssl/*.</span></span> <span data-ttu-id="740ba-120">Por exemplo, no Ubuntu 18, 4, o diretório é */usr/lib/SSL/Certs/* e o arquivo é */usr/lib/ssl/cert.pem*.</span><span class="sxs-lookup"><span data-stu-id="740ba-120">For example, on Ubuntu 18.04, the directory is */usr/lib/ssl/certs/* and the file is */usr/lib/ssl/cert.pem*.</span></span> <span data-ttu-id="740ba-121">No entanto, */usr/lib/SSL/Certs/* é um symlink para */etc/SSL/Certs/* e */usr/lib/ssl/cert.pem* não existe.</span><span class="sxs-lookup"><span data-stu-id="740ba-121">However, */usr/lib/ssl/certs/* is a symlink to */etc/ssl/certs/* and */usr/lib/ssl/cert.pem* does not exist.</span></span>

```bash
$ openssl version -d
OPENSSLDIR: "/usr/lib/ssl"
$ ls -al /usr/lib/ssl
total 12
drwxr-xr-x  3 root root 4096 Dec 12 17:10 .
drwxr-xr-x 73 root root 4096 Feb 20 15:18 ..
lrwxrwxrwx  1 root root   14 Mar 27  2018 certs -> /etc/ssl/certs
drwxr-xr-x  2 root root 4096 Dec 12 17:10 misc
lrwxrwxrwx  1 root root   20 Nov 12 16:58 openssl.cnf -> /etc/ssl/openssl.cnf
lrwxrwxrwx  1 root root   16 Mar 27  2018 private -> /etc/ssl/private
```

### <a name="category"></a><span data-ttu-id="740ba-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="740ba-122">Category</span></span>

<span data-ttu-id="740ba-123">Criptografia</span><span class="sxs-lookup"><span data-stu-id="740ba-123">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="740ba-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="740ba-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->

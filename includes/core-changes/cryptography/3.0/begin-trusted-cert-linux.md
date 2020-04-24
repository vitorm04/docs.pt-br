---
ms.openlocfilehash: 1d9a5bbea49730ee6cf99eaae6b20a0035e70b97
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135588"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>Sintaxe "BEGIN TRUSTed CERTIFICATE" não é mais suportada para certificados raiz no Linux

Os certificados raiz no Linux e em outros sistemas semelhantes a UNIX (mas não macOS) podem ser apresentados em duas formas: `BEGIN CERTIFICATE` o cabeçalho PEM padrão e o cabeçalho PEM `BEGIN TRUSTED CERTIFICATE` específico do OpenSSL. A última sintaxe permite uma configuração adicional que causou problemas de compatibilidade com a classe do <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> .NET Core. `BEGIN TRUSTED CERTIFICATE`o conteúdo do certificado raiz não é mais carregado pelo mecanismo de cadeia a partir do .NET Core 3,0.

#### <a name="change-description"></a>Descrição da alteração

Anteriormente, as `BEGIN CERTIFICATE` sintaxes `BEGIN TRUSTED CERTIFICATE` e foram usadas para popular a lista de confiança raiz. Se a `BEGIN TRUSTED CERTIFICATE` sintaxe tiver sido usada e opções adicionais tiverem sido especificadas no arquivo <xref:System.Security.Cryptography.X509Certificates.X509Chain> , talvez tenha relatado que a confiança da cadeia foi explicitamente despermitida<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>(). No entanto, se o certificado também tiver sido `BEGIN CERTIFICATE` especificado com a sintaxe em um arquivo carregado anteriormente, a cadeia de confiança era permitida.

A partir do .NET Core 3,0 `BEGIN TRUSTED CERTIFICATE` , o conteúdo não é mais lido. Se o certificado também não for especificado por meio de `BEGIN CERTIFICATE` uma sintaxe padrão <xref:System.Security.Cryptography.X509Certificates.X509Chain> , os relatórios que a raiz não é<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>confiável ().

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

A maioria dos aplicativos não é afetada por essa alteração, mas os aplicativos que não podem ver ambas as fontes de certificado raiz devido `UntrustedRoot` a problemas de permissões podem apresentar erros inesperados após a atualização.

Muitas distribuições do Linux (ou distribuições) gravam certificados raiz em dois locais: um diretório de um certificado por arquivo e uma concatenação de um arquivo. Em alguns distribuições, o diretório de um certificado por arquivo usa a `BEGIN TRUSTED CERTIFICATE` sintaxe enquanto a concatenação de arquivo usa a sintaxe padrão `BEGIN CERTIFICATE` . Certifique-se de que todos os certificados raiz `BEGIN CERTIFICATE` personalizados sejam adicionados como em pelo menos um desses locais e que ambos os locais possam ser lidos pelo seu aplicativo.

O diretório típico é */etc/SSL/Certs/* e o arquivo concatenado típico é */etc/ssl/cert.pem*. Use o comando `openssl version -d` para determinar a raiz específica da plataforma, que pode ser diferente de */etc/SSL/*. Por exemplo, no Ubuntu 18, 4, o diretório é */usr/lib/SSL/Certs/* e o arquivo é */usr/lib/ssl/cert.pem*. No entanto, */usr/lib/SSL/Certs/* é um symlink para */etc/SSL/Certs/* e */usr/lib/ssl/cert.pem* não existe.

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

### <a name="category"></a>Categoria

Criptografia

### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->

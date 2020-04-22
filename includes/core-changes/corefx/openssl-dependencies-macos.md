---
ms.openlocfilehash: 8790637c31d503455eb8ba722cca827c2a24b7c9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021470"
---
### <a name="openssl-versions-on-macos"></a>Versões openSSL no macOS

O .NET Core 3.0 e os tempos de execução posteriores no macOS agora preferem versões OpenSSL <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>1.1.x para as versões OpenSSL 1.0.x para <xref:System.Security.Cryptography.RSAOpenSsl>os <xref:System.Security.Cryptography.SafeEvpPKeyHandle> <xref:System.Security.Cryptography.AesCcm>tipos , <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, e,

O tempo de execução do .NET Core 2.1 agora suporta versões OpenSSL 1.1.x, mas ainda prefere versões OpenSSL 1.0.x.

#### <a name="change-description"></a>Descrição da alteração

Anteriormente, o tempo de execução do .NET Core usava versões OpenSSL 1.0.x no macOS para tipos que interagem com o OpenSSL. A versão mais recente do OpenSSL 1.0.x, OpenSSL 1.0.2, está agora sem suporte. Para manter os tipos que usam OpenSSL em versões suportadas do OpenSSL, o .NET Core 3.0 e os runtimes posteriores agora usam versões mais recentes do OpenSSL no macOS.

Com essa mudança, o comportamento dos tempos de execução do .NET Core no macOS é o seguinte:

- O .NET Core 3.0 e os runtimes posteriores da versão usam o OpenSSL 1.1.x, se disponível, e recuam para o OpenSSL 1.0.x apenas se não houver nenhuma versão 1.1.x disponível.

  Para os chamadores que usam os tipos de interop OpenSSL <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> com P/Invokes personalizados, siga as orientações nas observações. Seu aplicativo pode falhar se você <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> não verificar o valor.

- O tempo de execução do .NET Core 2.1 usa openssl 1.0.x, se disponível, e volta para openSSL 1.1.x se não houver nenhuma versão 1.0.x disponível.

  O tempo de execução 2.1 prefere a versão <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> anterior do OpenSSL porque a propriedade não existe no .NET Core 2.1, de modo que a versão OpenSSL não pode ser determinada de forma confiável no tempo de execução.

#### <a name="version-introduced"></a>Versão introduzida

- .NET Núcleo 2.1.16
- .NET Núcleo 3.0.3
- .NET Núcleo 3.1.2

#### <a name="recommended-action"></a>Ação recomendada

- Desinstale a versão 1.0.2 do OpenSSL se não for mais necessária.

- Instale o OpenSSL 1.1.x <xref:System.Security.Cryptography.DSAOpenSsl>se <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>você <xref:System.Security.Cryptography.RSAOpenSsl>usar <xref:System.Security.Cryptography.SafeEvpPKeyHandle> os <xref:System.Security.Cryptography.AesCcm>tipos , <xref:System.Security.Cryptography.AesGcm>, , ou , ou.

- Se você usar os tipos de interop OpenSSL com P/Invokes personalizados, siga as orientações nas <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> observações.

#### <a name="category"></a>Categoria

Bibliotecas Core .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->

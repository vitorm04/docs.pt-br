---
title: Modelo de Criptografia do .NET Framework
description: Examine as implementações de algoritmos de criptografia usuais no .NET. Aprenda o modelo de criptografia extensível de herança de objeto, design de fluxo & configuração.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: 11af4c15c8b291df898a3c2416faa15875eab70b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596313"
---
# <a name="net-framework-cryptography-model"></a>Modelo de Criptografia do .NET Framework

O .NET Framework fornece implementações de muitos algoritmos criptográficos padrão. Esses algoritmos são fáceis de usar e têm as propriedades padrão mais seguras possíveis. Além disso, o modelo de criptografia .NET Framework de herança de objeto, design de fluxo e configuração é extremamente extensível.

## <a name="object-inheritance"></a>Herança de objetos

O sistema de segurança .NET Framework implementa um padrão extensível de herança de classe derivada. A hierarquia é a seguinte:

- Classe de tipo de algoritmo, <xref:System.Security.Cryptography.SymmetricAlgorithm> como <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm> . Esse nível é abstrato.

- Classe de algoritmo que herda de uma classe de tipo de algoritmo; por exemplo, <xref:System.Security.Cryptography.Aes> , <xref:System.Security.Cryptography.RC2> ou <xref:System.Security.Cryptography.ECDiffieHellman> . Esse nível é abstrato.

- Implementação de uma classe de algoritmo que herda de uma classe de algoritmo; por exemplo, <xref:System.Security.Cryptography.AesManaged> , <xref:System.Security.Cryptography.RC2CryptoServiceProvider> ou <xref:System.Security.Cryptography.ECDiffieHellmanCng> . Esse nível é totalmente implementado.

Usando esse padrão de classes derivadas, é fácil adicionar um novo algoritmo ou uma nova implementação de um algoritmo existente. Por exemplo, para criar um novo algoritmo Public-Key, você herdaria da <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe. Para criar uma nova implementação de um algoritmo específico, você deve criar uma classe derivada não abstrata desse algoritmo.

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Como os algoritmos são implementados no .NET Framework

Como um exemplo das diferentes implementações disponíveis para um algoritmo, considere algoritmos simétricos. A base para todos os algoritmos simétricos é <xref:System.Security.Cryptography.SymmetricAlgorithm> , que é herdada pelos seguintes algoritmos:

* <xref:System.Security.Cryptography.Aes>
* <xref:System.Security.Cryptography.DES>
* <xref:System.Security.Cryptography.RC2>
* <xref:System.Security.Cryptography.Rijndael>
* <xref:System.Security.Cryptography.TripleDES>

<xref:System.Security.Cryptography.Aes>é herdado por duas classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> e <xref:System.Security.Cryptography.AesManaged> . A <xref:System.Security.Cryptography.AesCryptoServiceProvider> classe é um wrapper em relação à implementação da capi (API de criptografia do Windows) do AES, enquanto a <xref:System.Security.Cryptography.AesManaged> classe é inteiramente escrita em código gerenciado. Também há um terceiro tipo de implementação, CNG (Cryptography Next Generation), além das implementações gerenciadas e CAPI. Um exemplo de um algoritmo CNG é <xref:System.Security.Cryptography.ECDiffieHellmanCng> . Os algoritmos CNG estão disponíveis no Windows Vista e versões posteriores.

Você pode escolher qual implementação é a melhor para você. As implementações gerenciadas estão disponíveis em todas as plataformas que dão suporte a .NET Framework. As implementações de CAPI estão disponíveis em sistemas operacionais mais antigos e não são mais desenvolvidas. A CNG é a implementação mais recente em que o novo desenvolvimento ocorrerá. No entanto, as implementações gerenciadas não são certificadas pelo FIPS (Federal Information Processing Standards) e podem ser mais lentas do que as classes de wrapper.

## <a name="stream-design"></a>Design de fluxo

O Common Language Runtime usa um design orientado a fluxo para implementar algoritmos simétricos e algoritmos de hash. O núcleo desse design é a <xref:System.Security.Cryptography.CryptoStream> classe, que deriva da <xref:System.IO.Stream> classe. Os objetos criptográficos baseados em fluxo dão suporte a uma única interface padrão ( `CryptoStream` ) para manipular a parte de transferência de dados do objeto. Como todos os objetos são criados em uma interface padrão, você pode encadear vários objetos (como um objeto de hash seguido por um objeto de criptografia) e pode executar várias operações nos dados sem precisar de armazenamento intermediário para ele. O modelo de streaming também permite que você crie objetos de objetos menores. Por exemplo, um algoritmo combinado de criptografia e hash pode ser exibido como um único objeto de fluxo, embora esse objeto possa ser criado a partir de um conjunto de objetos de fluxo.

## <a name="cryptographic-configuration"></a>Configuração criptográfica

A configuração criptográfica permite que você resolva uma implementação específica de um algoritmo para um nome de algoritmo, permitindo a extensibilidade das classes de criptografia de .NET Framework. Você pode adicionar sua própria implementação de hardware ou software de um algoritmo e mapear a implementação para o nome do algoritmo de sua escolha. Se um algoritmo não for especificado no arquivo de configuração, as configurações padrão serão usadas. Para obter mais informações sobre a configuração de criptografia, consulte [Configurando classes de criptografia](../../framework/configure-apps/configure-cryptography-classes.md).

## <a name="choosing-an-algorithm"></a>Escolhendo um algoritmo

Você pode selecionar um algoritmo por diferentes motivos: por exemplo, para a integridade dos dados, para privacidade de dados ou para gerar uma chave. Algoritmos simétricos e de hash destinam-se à proteção de dados por motivos de integridade (proteção contra alterações) ou por motivos de privacidade (proteção contra a exibição). Algoritmos de hash são usados principalmente para integridade de dados.

Aqui está uma lista de algoritmos recomendados por aplicativo:

- Privacidade de dados:
  - <xref:System.Security.Cryptography.Aes>
- Integridade dos dados:
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- Assinatura digital:
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- Troca de chaves:
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- Geração de número aleatório:
  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>
- Gerando uma chave a partir de uma senha:
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>Consulte também

- [Serviços de Criptografia](cryptographic-services.md)
- [Protocolos de criptografia, algoritmos e código-fonte aplicados em C, de Bruce Schneier](https://www.schneier.com/books/applied_cryptography/)

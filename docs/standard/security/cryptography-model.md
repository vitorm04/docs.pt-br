---
title: Modelo de Criptografia do .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e39e9b3cf83be03d9bb3a55e3741915588e755a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499571"
---
# <a name="net-framework-cryptography-model"></a>Modelo de Criptografia do .NET Framework
O .NET Framework fornece implementações de muitos algoritmos criptográficos padrão. Esses algoritmos são fáceis de usar e têm as propriedades possíveis padrão mais seguras. Além disso, o modelo de criptografia do .NET Framework de herança de objetos, o design de fluxo e a configuração é extremamente extensível.  
  
## <a name="object-inheritance"></a>Herança de objetos  
 O sistema de segurança do .NET Framework implementa um padrão de herança de classe derivada de extensível. A hierarquia é da seguinte maneira:  
  
-   Classe de tipo de algoritmo, como <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm>. Esse nível é abstrata.  
  
-   Classe de algoritmo que herda de uma classe de tipo de algoritmo; Por exemplo, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, ou <xref:System.Security.Cryptography.ECDiffieHellman>. Esse nível é abstrata.  
  
-   Implementação de uma classe de algoritmo que herda de uma classe de algoritmo; Por exemplo, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, ou <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Esse nível é totalmente implementado.  
  
 Usando esse padrão de classes derivadas, é fácil adicionar um novo algoritmo ou uma nova implementação de um algoritmo existente. Por exemplo, para criar um novo algoritmo de chave pública, você herdaria a <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe. Para criar uma nova implementação de um algoritmo específico, você criaria uma classe derivada de não-abstrata de algoritmo.  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Como os algoritmos são implementados no .NET Framework  
 Por exemplo as diferentes implementações disponíveis para um algoritmo, considere algoritmos simétricos. É a base para todos os algoritmos simétricos <xref:System.Security.Cryptography.SymmetricAlgorithm>, que são herdadas pelos seguintes algoritmos:  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <xref:System.Security.Cryptography.Aes> é herdada por duas classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> e <xref:System.Security.Cryptography.AesManaged>. O <xref:System.Security.Cryptography.AesCryptoServiceProvider> classe é um wrapper em torno a implementação do Windows CAPI (Cryptography API) do Aes, enquanto o <xref:System.Security.Cryptography.AesManaged> classe é escrito totalmente em código gerenciado. Também há um terceiro tipo de implementação, geração de CNG (Cryptography Next), além de gerenciado e implementações de CAPI. Um exemplo de um algoritmo CNG é <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Algoritmos CNG estão disponíveis no Windows Vista e posterior.  
  
 Você pode escolher qual implementação é melhor para você.  As implementações gerenciadas estão disponíveis em todas as plataformas que dão suporte ao .NET Framework.  As implementações de CAPI estão disponíveis em sistemas operacionais mais antigos e não estão sendo desenvolvidas. A CNG é a implementação de muito mais recente em que novos desenvolvimentos ocorrerá. No entanto, as implementações gerenciadas não são certificadas pelo FIPS Federal Information Processing Standards () e podem ser mais lentas do que as classes de wrapper.  
  
## <a name="stream-design"></a>Design de Stream  
 O common language runtime usa um design orientado por fluxo para implementar algoritmos simétricos e algoritmos de hash. O núcleo desse design é o <xref:System.Security.Cryptography.CryptoStream> classe, que deriva de <xref:System.IO.Stream> classe. Com base no Stream criptográfico objetos dão suporte a uma interface padrão único (`CryptoStream`) para lidar com a parte da transferência de dados do objeto. Como todos os objetos são criados em uma interface padrão, você pode encadear vários objetos (como um objeto de hash, seguido por um objeto de criptografia) e você pode executar várias operações nos dados sem a necessidade de qualquer armazenamento intermediário para ele. O modelo de streaming também permite que você crie objetos desde objetos menores. Por exemplo, um algoritmo de criptografia e hash combinado pode ser exibido como um objeto de fluxo simples, embora esse objeto pode ser criado a partir de um conjunto de objetos de fluxo.  
  
## <a name="cryptographic-configuration"></a>Configuração criptográfica  
 A configuração criptográfica permite resolver uma implementação específica de um algoritmo para um nome de algoritmo, permitindo que a extensibilidade das classes de criptografia do .NET Framework. Você pode adicionar sua própria implementação de hardware ou software de um algoritmo e mapear a implementação para o nome do algoritmo de sua escolha. Se um algoritmo não é especificado no arquivo de configuração, as configurações padrão são usadas. Para obter mais informações sobre a configuração de criptografia, consulte [Configurando Classes de criptografia](../../../docs/framework/configure-apps/configure-cryptography-classes.md).  
  
## <a name="choosing-an-algorithm"></a>Escolhendo um algoritmo  
 Você pode selecionar um algoritmo por motivos diferentes: por exemplo, para a integridade de dados e privacidade de dados de ou para gerar uma chave. Algoritmos de hash e Symmetric destinam-se de proteger dados por motivos de integridade (proteção de alteração) ou motivos de privacidade (proteger contra a exibição). Algoritmos de hash são usados principalmente para a integridade dos dados.  
  
 Aqui está uma lista dos algoritmos recomendadas pelo aplicativo:  
  
-   Privacidade de dados:  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   Integridade de dados:  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   Assinatura digital:  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Troca de chaves:  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   Geração de números aleatórios:  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   Gerando uma chave de uma senha:  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a>Consulte também

- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)

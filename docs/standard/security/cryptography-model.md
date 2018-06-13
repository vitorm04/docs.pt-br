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
ms.openlocfilehash: ced7ed2cb8d3ae3bb24211c6e7dafd1744fb9559
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587450"
---
# <a name="net-framework-cryptography-model"></a>Modelo de Criptografia do .NET Framework
O .NET Framework fornece implementações de muitos algoritmos de criptografia padrão. Esses algoritmos são fáceis de usar e têm as propriedades possíveis padrão mais seguras. Além disso, o modelo de criptografia do .NET Framework de herança do objeto, o design do fluxo e a configuração é extremamente extensível.  
  
## <a name="object-inheritance"></a>Herança de objeto  
 O sistema de segurança do .NET Framework implementa um extensível padrão de herança de classe derivada. A hierarquia é o seguinte:  
  
-   Classe de tipo de algoritmo, como <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm>. Esse nível é abstrata.  
  
-   Classe de algoritmo que herda de uma classe de tipo de algoritmo; Por exemplo, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, ou <xref:System.Security.Cryptography.ECDiffieHellman>. Esse nível é abstrata.  
  
-   Implementação de uma classe de algoritmo que herda de uma classe de algoritmo; Por exemplo, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, ou <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Esse nível é totalmente implementado.  
  
 Usando esse padrão de classes derivadas, é fácil adicionar um novo algoritmo ou uma nova implementação de um algoritmo existente. Por exemplo, para criar um novo algoritmo de chave pública, você deve herdar do <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe. Para criar uma nova implementação de um algoritmo específico, você criaria uma classe derivada não-abstrato de algoritmo.  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>Como os algoritmos são implementados no .NET Framework  
 Como um exemplo das implementações diferentes disponíveis para um algoritmo, considere a possibilidade de algoritmos simétricos. É a base para todos os algoritmos simétricos <xref:System.Security.Cryptography.SymmetricAlgorithm>, que são herdadas pelos seguintes algoritmos:  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <xref:System.Security.Cryptography.Aes> é herdada por duas classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> e <xref:System.Security.Cryptography.AesManaged>. O <xref:System.Security.Cryptography.AesCryptoServiceProvider> classe é um wrapper para a implementação do Windows CAPI (Cryptography API) de Aes, enquanto o <xref:System.Security.Cryptography.AesManaged> classe escrita inteiramente em código gerenciado. Também há um terceiro tipo de implementação, geração de CNG (Cryptography Next), além de gerenciado e implementações de CAPI. Um exemplo de um algoritmo CNG é <xref:System.Security.Cryptography.ECDiffieHellmanCng>. Algoritmos CNG estão disponíveis no Windows Vista e versões posteriores.  
  
 Você pode escolher qual implementação é melhor para você.  As implementações gerenciadas estão disponíveis em todas as plataformas que dão suporte ao .NET Framework.  As implementações de CAPI estão disponíveis em sistemas operacionais mais antigos e não estão sendo desenvolvidas. A CNG é a implementação mais recente em novos desenvolvimentos ocorrerá. No entanto, as implementações gerenciadas não são certificadas pelo FIPS Federal Information Processing Standards () e podem ser mais lentas do que as classes de wrapper.  
  
## <a name="stream-design"></a>Design de fluxo  
 O common language runtime usa um design orientado por fluxo para a implementação de algoritmos simétricos e algoritmos de hash. O núcleo desse design é o <xref:System.Security.Cryptography.CryptoStream> classe que deriva de <xref:System.IO.Stream> classe. Com base em fluxo criptográfico objetos dão suporte a uma interface padrão único (`CryptoStream`) para lidar com a parte da transferência de dados do objeto. Como todos os objetos são criados em uma interface padrão, você pode encadear vários objetos (como um objeto de hash, seguido por um objeto de criptografia) e você pode executar várias operações nos dados sem a necessidade de qualquer armazenamento intermediário para ele. O modelo de streaming também permite que você crie objetos de objetos menores. Por exemplo, um algoritmo de criptografia e hash combinado pode ser exibido como um objeto de fluxo único, embora esse objeto pode ser criado a partir de um conjunto de objetos de fluxo.  
  
## <a name="cryptographic-configuration"></a>Configuração de criptografia  
 A configuração criptográfica permite resolver uma implementação específica de um algoritmo para um nome de algoritmo, permitindo a extensibilidade de classes de criptografia do .NET Framework. Você pode adicionar sua própria implementação de hardware ou software de um algoritmo e a implementação do mapa para o nome do algoritmo de sua escolha. Se um algoritmo não é especificado no arquivo de configuração, as configurações padrão são usadas. Para obter mais informações sobre a configuração de criptografia, consulte [Configurando Classes de criptografia](../../../docs/framework/configure-apps/configure-cryptography-classes.md).  
  
## <a name="choosing-an-algorithm"></a>Escolhendo um algoritmo  
 Você pode selecionar um algoritmo por diferentes motivos: por exemplo, para a integridade de dados, à privacidade dos dados ou para gerar uma chave. Algoritmos de hash e Symmetric destinam-se para proteger dados por motivos de integridade (proteção de alteração) ou motivos de privacidade (proteção de exibição). Algoritmos de hash são usados principalmente para a integridade dos dados.  
  
 Aqui está uma lista dos algoritmos recomendados pelo aplicativo:  
  
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
  
-   Gerar uma chave de uma senha:  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a>Consulte também  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)  
 

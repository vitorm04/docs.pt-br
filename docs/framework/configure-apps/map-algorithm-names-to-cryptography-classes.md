---
title: Mapeando nomes de algoritmo para classes de criptografia
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
author: mcleblanc
ms.author: markl
ms.openlocfilehash: cd57cc7bbe39b042e11d0dad3fd54373bcaae98b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196233"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Mapeando nomes de algoritmo para classes de criptografia
Há quatro maneiras que um desenvolvedor pode criar um objeto de criptografia usando o [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   Criar um objeto usando o **novo** operador.  
  
-   Criar um objeto que implementa um algoritmo de criptografia específica chamando o **criar** método na classe abstrata para esse algoritmo.  
  
-   Criar um objeto que implementa um algoritmo de criptografia específica chamando o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método.  
  
-   Criar um objeto que implementa uma classe de algoritmos criptográficos (como uma codificação de bloco simétrica) chamando o **Create** método na classe abstrata para esse tipo de algoritmo (como <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 Por exemplo, suponha que um desenvolvedor deseja calcular o hash SHA1 de um conjunto de bytes. O <xref:System.Security.Cryptography> namespace contém duas implementações do algoritmo SHA1, uma implementação totalmente gerenciada e outro que encapsula o CryptoAPI. O desenvolvedor pode optar por criar uma instância de uma implementação específica do SHA1 (como o <xref:System.Security.Cryptography.SHA1Managed>) chamando o **nova** operador. No entanto, se ele não importa qual classe o common language runtime carrega desde que a classe implementa o algoritmo de hash SHA1, o desenvolvedor pode criar um objeto chamando o <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> método. Este método chama **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, que deve retornar uma implementação do algoritmo de hash SHA1.  
  
 O desenvolvedor também pode chamar **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** porque, por padrão, a configuração de criptografia inclui nomes curtos para os algoritmos fornecidos no .NET Framework.  
  
 Se não importa qual algoritmo de hash é usado, o desenvolvedor pode chamar o <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> método, que retorna um objeto que implementa uma transformação de hash.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Mapeando nomes de algoritmo em arquivos de configuração  
 Por padrão, o tempo de execução retorna um <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objeto para todos os quatro cenários. No entanto, um administrador do computador pode alterar o tipo de objeto que retornam os métodos nos últimos dois cenários. Para fazer isso, você deve mapear um nome de algoritmo amigável para a classe que você deseja usar no arquivo de configuração do computador (Machine. config).  
  
 O exemplo a seguir mostra como configurar o tempo de execução para que **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, e  **System.Security.Cryptography.HashAlgorithm.Create** retornar uma `MySHA1HashClass` objeto.  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 Você pode especificar o nome do atributo na [< cryptoClass\> elemento](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (o exemplo anterior nomeia o atributo `MySHA1Hash`). O valor do atributo na  **\<cryptoClass >** elemento é uma cadeia de caracteres que o common language runtime usa para encontrar a classe. Você pode usar qualquer cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Muitos nomes de algoritmo podem mapear para a mesma classe. O [ \<nameEntry > elemento](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mapeia uma classe para um nome de algoritmo amigáveis. O **nome** atributo pode ser uma cadeia de caracteres que é usada ao chamar o **System.Security.Cryptography.CryptoConfig.CreateFromName** método ou o nome de uma classe abstrata de criptografia no <xref:System.Security.Cryptography> namespace. O valor da **classe** atributo é o nome do atributo na  **\<cryptoClass >** elemento.  
  
> [!NOTE]
>  Você pode obter um algoritmo SHA1 chamando o <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> ou o **Security.CryptoConfig.CreateFromName("SHA1")** método. Cada método apenas garante que ele retorna um objeto que implementa o algoritmo SHA1. Você não precisa mapear cada nome amigável de um algoritmo para a mesma classe no arquivo de configuração.  
  
 Para obter uma lista de nomes padrão e as classes que são mapeados, consulte <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)  
 [Configurando classes de criptografia](../../../docs/framework/configure-apps/configure-cryptography-classes.md)

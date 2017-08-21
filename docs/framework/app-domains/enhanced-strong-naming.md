---
title: "Nomeação forte aprimorada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 429a54340cef6d608692abd71311c012afe9a3d0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="enhanced-strong-naming"></a>Nomeação forte aprimorada
Uma assinatura de nome forte é um mecanismo de identidade no .NET Framework para identificar os assemblies. É uma assinatura digital de chave pública que normalmente é usada para verificar a integridade dos dados que são passados de um remetente (assinante) para um destinatário (verificador). Essa assinatura é usada como uma identidade exclusiva para um assembly e garante que as referências ao assembly não sejam ambíguas. O assembly é assinado como parte do processo de compilação e verificado ao ser carregado.  
  
 Assinaturas de nome forte ajudam a impedir que pessoas mal-intencionadas adulterem um assembly e assinem novamente o assembly com a chave do assinante original. No entanto, as chaves de nome forte não contêm informações confiáveis sobre o publicador, nem contém uma hierarquia de certificados. Uma assinatura de nome forte não garante a confiabilidade da pessoa que assinou o assembly, nem indica se a pessoa era um proprietário legítimo da chave, indicando apenas que o proprietário da chave assinou o assembly. Portanto, não recomendamos usar uma assinatura de nome forte como um validador de segurança para confiar em código de terceiros. O Microsoft Authenticode é a maneira recomendada para autenticar o código.  
  
## <a name="limitations-of-conventional-strong-names"></a>Limitações de nomes fortes convencionais  
 A tecnologia de nomeação forte usada nas versões anteriores ao [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] têm as seguintes limitações:  
  
-   As chaves estão constantemente sendo atacadas e as técnicas e o hardware aprimorados facilitam a inferência de uma chave privada com base em uma chave pública. Para se proteger contra ataques, chaves maiores são necessárias. Versões do .NET framework anteriores ao [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] fornecem a capacidade de assinar com chaves de qualquer tamanho (o tamanho padrão é 1024 bits), mas assinar um assembly com uma nova chave interrompe todos os binários que fazem referência à identidade mais antiga do assembly. Portanto, é extremamente difícil atualizar o tamanho de uma chave de assinatura se você desejar manter a compatibilidade.  
  
-   A assinatura de nome forte dá suporte apenas ao algoritmo SHA-1. Recentemente, foi descoberto que o SHA-1 é inadequado para aplicativos de hash seguros. Portanto, um algoritmo mais forte (SHA-256 ou superior) é necessário. É possível que o SHA-1 perca sua posição de conformidade com o FIPS, o que causaria problemas para aqueles que optarem por usar somente os algoritmos e software em conformidade com FIPS.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Vantagens de nomes fortes aprimorados  
 As principais vantagens de nomes fortes aprimorados são compatibilidade com nomes fortes já existentes e a capacidade de declarar que uma identidade é equivalente a outra:  
  
-   Os desenvolvedores que têm assemblies assinados pré-existentes podem migrar suas identidades para os algoritmos SHA-2 enquanto mantém a compatibilidade com os assemblies que referenciam as identidades antigas.  
  
-   Desenvolvedores que criam novos assemblies e não se preocupam com assinaturas de nome forte pre-existente podem usar os algoritmos SHA-2 mais seguros e assinar os assemblies como de costume.  
  
## <a name="using-enhanced-strong-names"></a>Usando nomes fortes aprimorados  
 Chaves de nome forte consistem em uma chave de assinatura e uma chave de identidade. O assembly é assinado com a chave de assinatura e é identificado pela chave de identidade. Antes do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], essas duas chaves eram idênticas. A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], a chave de identidade permanece a mesma que nas versões anteriores do .NET Framework, mas a chave de assinatura foi aprimorada com um algoritmo de hash mais forte. Além disso, a chave de assinatura é assinada com a chave de identidade para criar uma referenda.  
  
 O atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> permite que os metadados de assembly usem a chave pública pré-existente para a identidade do assembly, permitindo que referências ao assembly antigo continuem a funcionar.  O atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> usa a referenda para garantir que o proprietário da nova chave de assinatura também seja o proprietário da chave de identidade antiga.  
  
### <a name="signing-with-sha-2-without-key-migration"></a>Assinar com SHA-2 sem migração de chave  
 Execute os seguintes comandos em uma janela do Prompt de comando para assinar um assembly sem migrar uma assinatura de nome forte:  
  
1.  Gere a nova chave de identidade (se necessário).  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  Extraia a chave pública de identidade e especifique que um algoritmo SHA-2 deve ser usado ao assinar com essa chave.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  Assine com atraso o assembly com o arquivo de chave pública de identidade.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  Assine novamente o assembly com o par de chaves de identidade completa.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>Assinar com SHA-2 com migração de chave  
 Execute os seguintes comandos em uma janela de Prompt de comando para assinar um assembly com uma assinatura de nome forte migrado.  
  
1.  Gere um par de chaves de identidade e de assinatura (se necessário).  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  Extraia a chave pública de assinatura e especifique que um algoritmo SHA-2 deve ser usado ao assinar com essa chave.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  Extraia a chave pública de identidade, que determina o algoritmo de hash que gera uma referenda.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  Gere os parâmetros para um atributo <xref:System.Reflection.AssemblySignatureKeyAttribute> e, em seguida, anexe o atributo ao assembly.  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  Assine com atraso o assembly com a chave pública de identidade.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  Assine completamente o assembly com o par de chaves de assinatura.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Criar e usar assemblies de nomes fortes](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)


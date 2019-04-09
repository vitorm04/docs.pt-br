---
title: Mapeando identificadores de objeto para algoritmos de criptografia
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e035ff04a70a441f7f64bbc230ba6d8036fb2ace
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130605"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Mapeando identificadores de objeto para algoritmos de criptografia
Assinaturas digitais Certifique-se de que dados não seja violados quando ela é enviada de um programa para outro. Normalmente, a assinatura digital é computada, aplicando uma função matemática para o hash dos dados a serem assinados. Ao formatar um valor de hash a ser assinada, alguns algoritmos de assinatura digital acrescentar um ASN. 1 objeto OID (identificador) como parte da operação de formatação. O OID identifica o algoritmo que foi usado para computar o hash. Você pode mapear os algoritmos para identificadores de objeto para estender o mecanismo de criptografia para usar algoritmos personalizados. O exemplo a seguir mostra como mapear um identificador de objeto para um novo algoritmo de hash.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 O [ \<oidEntry > elemento](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contém dois atributos. O **OID** atributo é o número de identificador de objeto. O **nome** atributo é o valor da **nome** de atributos dos [ \<nameEntry > elemento](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md). Deve haver um mapeamento de um nome de algoritmo para uma classe antes de um identificador de objeto pode ser mapeado para um nome simples.  
  
## <a name="see-also"></a>Consulte também

- [Configurando classes de criptografia](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)

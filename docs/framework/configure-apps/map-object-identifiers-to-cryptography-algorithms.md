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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7801c55cf6b3334347788013d9052038d5d2f3ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756612"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="5d4b2-102">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="5d4b2-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="5d4b2-103">Assinaturas digitais Certifique-se de que dados não foi violados quando ela é enviada de um programa para outro.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="5d4b2-104">Normalmente a assinatura digital é calculada pela aplicação de uma função matemática para o hash de dados a ser assinado.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="5d4b2-105">Ao formatar um valor de hash a ser assinada, alguns algoritmos de assinatura digital acrescentar um identificador de objeto de ASN. 1 (OID) como parte da operação de formatação.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="5d4b2-106">O OID identifica o algoritmo que foi usado para calcular o hash.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="5d4b2-107">Você pode mapear os algoritmos para identificadores de objeto para estender o mecanismo de criptografia para usar algoritmos personalizados.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="5d4b2-108">O exemplo a seguir mostra como mapear um identificador de objeto para um novo algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="5d4b2-109">O [ \<oidEntry > elemento](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contém dois atributos.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="5d4b2-110">O **OID** atributo é o número do identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="5d4b2-111">O **nome** atributo é o valor da **nome** de atributo do [ \<nameEntry > elemento](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="5d4b2-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="5d4b2-112">Deve haver um mapeamento de um nome de algoritmo para uma classe antes de um identificador de objeto pode ser mapeado para um nome simples.</span><span class="sxs-lookup"><span data-stu-id="5d4b2-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4b2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d4b2-113">See Also</span></span>  
 [<span data-ttu-id="5d4b2-114">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="5d4b2-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="5d4b2-115">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="5d4b2-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

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
ms.openlocfilehash: a5aebac2d392d4540581dfe7c7afff0819968ac0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912536"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="46fd7-102">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="46fd7-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="46fd7-103">As assinaturas digitais garantem que os dados não sejam adulterados quando enviados de um programa para outro.</span><span class="sxs-lookup"><span data-stu-id="46fd7-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="46fd7-104">Normalmente, a assinatura digital é computada aplicando uma função matemática ao hash dos dados a serem assinados.</span><span class="sxs-lookup"><span data-stu-id="46fd7-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="46fd7-105">Ao Formatar um valor de hash a ser assinado, alguns algoritmos de assinatura digital acrescentam um OID (identificador de objeto) de ASN. 1 como parte da operação de formatação.</span><span class="sxs-lookup"><span data-stu-id="46fd7-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="46fd7-106">O OID identifica o algoritmo que foi usado para calcular o hash.</span><span class="sxs-lookup"><span data-stu-id="46fd7-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="46fd7-107">Você pode mapear algoritmos para identificadores de objeto para estender o mecanismo de criptografia para usar algoritmos personalizados.</span><span class="sxs-lookup"><span data-stu-id="46fd7-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="46fd7-108">O exemplo a seguir mostra como mapear um identificador de objeto para um novo algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="46fd7-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="46fd7-109">[ O\<elemento > oidEntry](./file-schema/cryptography/oidentry-element.md) contém dois atributos.</span><span class="sxs-lookup"><span data-stu-id="46fd7-109">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="46fd7-110">O atributo **OID** é o número do identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="46fd7-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="46fd7-111">O atributo **Name** é o valor do [ \<atributo Name do elemento > nameEntry](./file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="46fd7-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="46fd7-112">Deve haver um mapeamento de um nome de algoritmo para uma classe antes que um identificador de objeto possa ser mapeado para um nome simples.</span><span class="sxs-lookup"><span data-stu-id="46fd7-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46fd7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46fd7-113">See also</span></span>

- [<span data-ttu-id="46fd7-114">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="46fd7-114">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="46fd7-115">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="46fd7-115">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)

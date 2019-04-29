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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775772"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="2147e-102">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="2147e-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="2147e-103">Assinaturas digitais Certifique-se de que dados não seja violados quando ela é enviada de um programa para outro.</span><span class="sxs-lookup"><span data-stu-id="2147e-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="2147e-104">Normalmente, a assinatura digital é computada, aplicando uma função matemática para o hash dos dados a serem assinados.</span><span class="sxs-lookup"><span data-stu-id="2147e-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="2147e-105">Ao formatar um valor de hash a ser assinada, alguns algoritmos de assinatura digital acrescentar um ASN. 1 objeto OID (identificador) como parte da operação de formatação.</span><span class="sxs-lookup"><span data-stu-id="2147e-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="2147e-106">O OID identifica o algoritmo que foi usado para computar o hash.</span><span class="sxs-lookup"><span data-stu-id="2147e-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="2147e-107">Você pode mapear os algoritmos para identificadores de objeto para estender o mecanismo de criptografia para usar algoritmos personalizados.</span><span class="sxs-lookup"><span data-stu-id="2147e-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="2147e-108">O exemplo a seguir mostra como mapear um identificador de objeto para um novo algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="2147e-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="2147e-109">O [ \<oidEntry > elemento](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contém dois atributos.</span><span class="sxs-lookup"><span data-stu-id="2147e-109">The [\<oidEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="2147e-110">O **OID** atributo é o número de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="2147e-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="2147e-111">O **nome** atributo é o valor da **nome** de atributos dos [ \<nameEntry > elemento](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="2147e-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="2147e-112">Deve haver um mapeamento de um nome de algoritmo para uma classe antes de um identificador de objeto pode ser mapeado para um nome simples.</span><span class="sxs-lookup"><span data-stu-id="2147e-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2147e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2147e-113">See also</span></span>

- [<span data-ttu-id="2147e-114">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="2147e-114">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="2147e-115">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="2147e-115">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

---
title: Criando um esquema criptográfico
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1635276465dd58028c8a5e4b7e69a307664a4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580751"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="de0b2-102">Criando um esquema criptográfico</span><span class="sxs-lookup"><span data-stu-id="de0b2-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="de0b2-103">Os componentes de criptografia do .NET Framework podem ser combinados para criar esquemas diferentes para criptografar e descriptografar dados.</span><span class="sxs-lookup"><span data-stu-id="de0b2-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="de0b2-104">Um simple esquema de criptografia para criptografar e descriptografar dados pode especificar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="de0b2-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="de0b2-105">Cada parte gera um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="de0b2-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="de0b2-106">As partes trocam suas chaves públicas.</span><span class="sxs-lookup"><span data-stu-id="de0b2-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="de0b2-107">Cada parte gera uma chave secreta de criptografia TripleDES, por exemplo e criptografa a chave recém-criada usando a chave pública do outro.</span><span class="sxs-lookup"><span data-stu-id="de0b2-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="de0b2-108">Cada parte envia os dados para outro e combina a chave secreta do outro com seu próprio, em uma determinada ordem, para criar uma nova chave secreta.</span><span class="sxs-lookup"><span data-stu-id="de0b2-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="de0b2-109">As partes, em seguida, iniciam uma conversa usando a criptografia simétrica.</span><span class="sxs-lookup"><span data-stu-id="de0b2-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="de0b2-110">Criando um esquema de criptografia não é uma tarefa fácil.</span><span class="sxs-lookup"><span data-stu-id="de0b2-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="de0b2-111">Para obter mais informações sobre o uso de criptografia, consulte o tópico de criptografia na documentação do SDK da plataforma em http://msdn.microsoft.com/library.</span><span class="sxs-lookup"><span data-stu-id="de0b2-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de0b2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de0b2-112">See Also</span></span>  
 [<span data-ttu-id="de0b2-113">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="de0b2-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

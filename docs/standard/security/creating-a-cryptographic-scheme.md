---
title: "Criando um esquema criptográfico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e3c4a832f70fae7808bf71016cb9f6648332f01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="5f5b5-102">Criando um esquema criptográfico</span><span class="sxs-lookup"><span data-stu-id="5f5b5-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="5f5b5-103">Os componentes de criptografia do .NET Framework podem ser combinados para criar esquemas diferentes para criptografar e descriptografar dados.</span><span class="sxs-lookup"><span data-stu-id="5f5b5-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="5f5b5-104">Um simple esquema de criptografia para criptografar e descriptografar dados pode especificar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="5f5b5-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="5f5b5-105">Cada parte gera um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="5f5b5-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="5f5b5-106">As partes trocam suas chaves públicas.</span><span class="sxs-lookup"><span data-stu-id="5f5b5-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="5f5b5-107">Cada parte gera uma chave secreta de criptografia TripleDES, por exemplo e criptografa a chave recém-criada usando a chave pública do outro.</span><span class="sxs-lookup"><span data-stu-id="5f5b5-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="5f5b5-108">Cada parte envia os dados para outro e combina a chave secreta do outro com seu próprio, em uma determinada ordem, para criar uma nova chave secreta.</span><span class="sxs-lookup"><span data-stu-id="5f5b5-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="5f5b5-109">As partes, em seguida, iniciam uma conversa usando a criptografia simétrica.</span><span class="sxs-lookup"><span data-stu-id="5f5b5-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="5f5b5-110">Criando um esquema de criptografia não é uma tarefa fácil.</span><span class="sxs-lookup"><span data-stu-id="5f5b5-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="5f5b5-111">Para obter mais informações sobre o uso de criptografia, consulte o tópico de criptografia na documentação do SDK da plataforma em http://msdn.microsoft.com/library.</span><span class="sxs-lookup"><span data-stu-id="5f5b5-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5b5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f5b5-112">See Also</span></span>  
 [<span data-ttu-id="5f5b5-113">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="5f5b5-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

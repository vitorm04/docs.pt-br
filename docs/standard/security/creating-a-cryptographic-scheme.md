---
title: Criando um esquema criptográfico
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288414"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="bac9f-102">Criando um esquema criptográfico</span><span class="sxs-lookup"><span data-stu-id="bac9f-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="bac9f-103">Os componentes de criptografia do .NET Framework podem ser combinados para criar esquemas diferentes para criptografar e descriptografar dados.</span><span class="sxs-lookup"><span data-stu-id="bac9f-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="bac9f-104">Um esquema criptográfico simples para criptografar e descriptografar dados pode especificar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="bac9f-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1. <span data-ttu-id="bac9f-105">Cada parte gera um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="bac9f-105">Each party generates a public/private key pair.</span></span>  
  
2. <span data-ttu-id="bac9f-106">As partes trocam suas chaves públicas.</span><span class="sxs-lookup"><span data-stu-id="bac9f-106">The parties exchange their public keys.</span></span>  
  
3. <span data-ttu-id="bac9f-107">Cada parte gera uma chave secreta para criptografia TripleDES, por exemplo, e criptografa a chave recém-criada usando a chave pública do outro.</span><span class="sxs-lookup"><span data-stu-id="bac9f-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4. <span data-ttu-id="bac9f-108">Cada parte envia os dados para o outro e combina a chave secreta da outra com sua própria, em uma ordem específica, para criar uma nova chave secreta.</span><span class="sxs-lookup"><span data-stu-id="bac9f-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5. <span data-ttu-id="bac9f-109">Em seguida, as partes iniciam uma conversa usando a criptografia simétrica.</span><span class="sxs-lookup"><span data-stu-id="bac9f-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="bac9f-110">A criação de um esquema criptográfico não é uma tarefa trivial.</span><span class="sxs-lookup"><span data-stu-id="bac9f-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bac9f-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="bac9f-111">See also</span></span>

- [<span data-ttu-id="bac9f-112">Serviços de Criptografia</span><span class="sxs-lookup"><span data-stu-id="bac9f-112">Cryptographic Services</span></span>](cryptographic-services.md)

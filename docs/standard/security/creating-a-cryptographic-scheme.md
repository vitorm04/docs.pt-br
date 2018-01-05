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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b0aabdc9150aea73ad9078b0e9ee92b2abd03e17
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="creating-a-cryptographic-scheme"></a>Criando um esquema criptográfico
Os componentes de criptografia do .NET Framework podem ser combinados para criar esquemas diferentes para criptografar e descriptografar dados.  
  
 Um simple esquema de criptografia para criptografar e descriptografar dados pode especificar as seguintes etapas:  
  
1.  Cada parte gera um par de chaves pública/privada.  
  
2.  As partes trocam suas chaves públicas.  
  
3.  Cada parte gera uma chave secreta de criptografia TripleDES, por exemplo e criptografa a chave recém-criada usando a chave pública do outro.  
  
4.  Cada parte envia os dados para outro e combina a chave secreta do outro com seu próprio, em uma determinada ordem, para criar uma nova chave secreta.  
  
5.  As partes, em seguida, iniciam uma conversa usando a criptografia simétrica.  
  
 Criando um esquema de criptografia não é uma tarefa fácil. Para obter mais informações sobre o uso de criptografia, consulte o tópico de criptografia na documentação do SDK da plataforma em http://msdn.microsoft.com/library.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)

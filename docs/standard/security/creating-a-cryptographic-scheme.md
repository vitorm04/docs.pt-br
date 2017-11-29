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

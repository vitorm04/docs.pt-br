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
ms.openlocfilehash: 2db6d4229ac777801aff792c86fe0e5e9a1b4994
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45653285"
---
# <a name="creating-a-cryptographic-scheme"></a>Criando um esquema criptográfico
Os componentes de criptografia do .NET Framework podem ser combinados para criar esquemas diferentes para criptografar e descriptografar dados.  
  
 Um esquema simple de criptografia para criptografar e descriptografar dados pode especificar as seguintes etapas:  
  
1.  Cada parte gera um par de chaves pública/privada.  
  
2.  As partes trocam suas chaves públicas.  
  
3.  Cada parte gera uma chave secreta de criptografia TripleDES, por exemplo e criptografa a chave criada recentemente usando a chave pública do outro.  
  
4.  Cada parte envia os dados para outro e combina a chave secreta do outro com por conta própria, em uma determinada ordem, para criar uma nova chave secreta.  
  
5.  As partes, em seguida, iniciam uma conversa usando a criptografia simétrica.  
  
 Criando um esquema de criptografia não é uma tarefa trivial. Para obter mais informações sobre como usar criptografia, consulte o tópico de criptografia na documentação do SDK da plataforma em http://msdn.microsoft.com/library.  
  
## <a name="see-also"></a>Consulte também

- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)

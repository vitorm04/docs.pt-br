---
title: Criando um esquema criptográfico
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 00fff5f346633a9682d75cf6a3be7e8e7d5db7e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706286"
---
# <a name="creating-a-cryptographic-scheme"></a>Criando um esquema criptográfico
Os componentes de criptografia do .NET Framework podem ser combinados para criar esquemas diferentes para criptografar e descriptografar dados.  
  
 Um esquema criptográfico simples para criptografar e descriptografar dados pode especificar as seguintes etapas:  
  
1. Cada parte gera um par de chaves pública/privada.  
  
2. As partes trocam suas chaves públicas.  
  
3. Cada parte gera uma chave secreta para criptografia TripleDES, por exemplo, e criptografa a chave recém-criada usando a chave pública do outro.  
  
4. Cada parte envia os dados para o outro e combina a chave secreta da outra com sua própria, em uma ordem específica, para criar uma nova chave secreta.  
  
5. Em seguida, as partes iniciam uma conversa usando a criptografia simétrica.  
  
 A criação de um esquema criptográfico não é uma tarefa trivial.
  
## <a name="see-also"></a>Veja também

- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)

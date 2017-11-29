---
title: "Assegurando a integridade dos dados com códigos hash"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b5d54a608ae87a1b453b4fa2b4b351ac5fc9f068
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Assegurando a integridade dos dados com códigos hash
Um valor de hash é um valor numérico de comprimento fixo que identifica exclusivamente a dados. Valores de hash representam grandes quantidades de dados como valores numéricos muito menores, para que eles são usados com assinaturas digitais. Você pode assinar um valor de hash de forma mais eficiente que o maior valor de assinatura. Valores de hash também são úteis para verificar a integridade dos dados enviados por meio de canais inseguras. O valor de hash de dados recebidos pode ser comparado com o valor de hash de dados como ele foi enviado para determinar se os dados foi alterados.  
  
 Este tópico descreve como gerar e verificar códigos hash usando as classes de <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.  
  
## <a name="generating-a-hash"></a>Gerando um Hash  
 As classes de hash gerenciado podem hash de uma matriz de bytes ou um objeto de fluxo gerenciados. O exemplo a seguir usa o algoritmo de hash SHA1 para criar um valor de hash para uma cadeia de caracteres. O exemplo usa o <xref:System.Text.UnicodeEncoding> classe para converter a cadeia de caracteres em uma matriz de bytes que são transformadas em hash usando o <xref:System.Security.Cryptography.SHA1Managed> classe. O valor de hash é exibido no console.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Esse código exibirá a seguinte cadeia de caracteres para o console:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Verificando um Hash  
 Dados podem ser comparados com um valor de hash para determinar sua integridade. Geralmente, dados é transformado em hash em uma determinada hora e o valor de hash é protegido de alguma forma. Em um momento posterior, os dados podem ser misturados novamente e comparados com o valor protegido. Se os valores de hash coincidirem, os dados não foi alterados. Se os valores não coincidirem, os dados foi corrompidos. Para este sistema de trabalho, o hash protegido deve ser criptografado ou mantido em segredo de todas as partes não confiáveis.  
  
 O exemplo a seguir compara o valor de hash anterior de uma cadeia de caracteres para um novo valor de hash. Este exemplo executa um loop em cada byte de valores de hash e faz uma comparação.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Se os dois valores de hash coincidirem, este código exibe o seguinte no console:  
  
```  
The hash codes match.  
```  
  
 Se eles não coincidirem, o código exibe o seguinte:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Consulte também  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)

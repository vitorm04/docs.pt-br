---
title: Assegurando a integridade dos dados com códigos hash
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075579"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Assegurando a integridade dos dados com códigos hash
Um valor de hash é um valor numérico de comprimento fixo que identifica exclusivamente a dados. Valores de hash representam grandes quantidades de dados como valores numéricos muito menores, para que eles são usados com assinaturas digitais. Você pode assinar um valor de hash de forma mais eficiente que o maior valor de assinatura. Valores de hash também são úteis para verificar a integridade dos dados enviados por meio de canais inseguros. O valor de hash dos dados recebidos pode ser comparado com o valor de hash de dados como ele foi enviado para determinar se os dados foi alterados.  
  
 Este tópico descreve como gerar e verificar códigos hash usando as classes de <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.  
  
## <a name="generating-a-hash"></a>Gerar um Hash  
 As classes de hash gerenciados podem discutir uma matriz de bytes ou um objeto de fluxo gerenciado. O exemplo a seguir usa o algoritmo de hash SHA1 para criar um valor de hash para uma cadeia de caracteres. O exemplo usa o <xref:System.Text.UnicodeEncoding> classe para converter a cadeia de caracteres em uma matriz de bytes que são transformadas em hash usando o <xref:System.Security.Cryptography.SHA1Managed> classe. O valor de hash é exibido no console.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Esse código exibirá a seguinte cadeia de caracteres no console:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Verificando um Hash  
 Dados podem ser comparados a um valor de hash para determinar sua integridade. Normalmente, os dados é transformado em hash em um determinado momento e o valor de hash é protegido de alguma forma. Em um momento posterior, os dados podem ser transformada em hash novamente e comparado com o valor protegido. Se os valores de hash corresponderem, os dados não foram alterados. Se os valores não corresponderem, os dados foi corrompidos. Para este sistema funcione, o hash protegido deve ser criptografado ou mantido em segredo de todas as partes não confiáveis.  
  
 O exemplo a seguir compara o valor de hash anterior de uma cadeia de caracteres para um novo valor de hash. Este exemplo executa um loop em cada byte dos valores de hash e faz uma comparação.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Se dois valores de hash corresponderem, esse código exibe o seguinte no console:  
  
```  
The hash codes match.  
```  
  
 Se eles não corresponderem, o código exibe o seguinte:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Consulte também

- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)

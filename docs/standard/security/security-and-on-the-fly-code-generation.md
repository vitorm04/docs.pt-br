---
title: Segurança e geração de código durante a execução
description: Gerar código em nome de código de menor confiança que é executado em uma confiança superior é uma preocupação de segurança, especialmente quando um chamador pode influenciar a geração de código.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 34ebda27a81ca29ebb27a721b77b735a12be882e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186794"
---
# <a name="security-and-on-the-fly-code-generation"></a>Segurança e geração de código durante a execução
Algumas bibliotecas operam gerando código e executando-o para executar alguma operação para o chamador. O problema básico é gerar código em nome de código de menor confiança e executá-lo em uma confiança superior. O problema se agrava quando o chamador pode influenciar a geração de código, então você deve garantir que apenas o código que você considera seguro seja gerado.  
  
 Você precisa saber exatamente que código você está gerando o tempo todo. Isso significa que você deve ter controles rigorosos sobre quaisquer valores que você obtenha de um usuário, sejam eles strings fechados com aspas (que devem ser escapadas para que eles não possam incluir elementos de código inesperados), identificadores (que devem ser verificados para verificar se eles são válidos identificadores), ou qualquer outra coisa. Os identificadores podem ser perigosos porque um conjunto compilado pode ser modificado para que seus identificadores contenham caracteres estranhos, o que provavelmente irá quebrá-lo (embora isso raramente seja uma vulnerabilidade de segurança).  
  
 Recomenda-se que você gere código com eitação de reflexão, o que muitas vezes ajuda a evitar muitos desses problemas.  
  
 Ao compilar o código, considere se há alguma maneira de um programa malicioso modificá-lo. Existe uma pequena janela de tempo durante a qual o código malicioso pode alterar o código-fonte no disco antes que o compilador o leia ou antes que seu código carregue o arquivo .dll? Nesse caso, você deve proteger o diretório que contém esses arquivos, usando uma Lista de Controle de Acesso no sistema de arquivos, conforme apropriado.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)

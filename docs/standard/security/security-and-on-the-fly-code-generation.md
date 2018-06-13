---
title: Segurança e geração de código durante a execução
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cfc93e1c8d3d9e878d96de164b0d646e62c0998
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583962"
---
# <a name="security-and-on-the-fly-code-generation"></a>Segurança e geração de código durante a execução
Algumas bibliotecas operam por geração de código e executá-lo para executar alguma operação para o chamador. O problema básico está gerando o código em nome do código de confiança menor e executá-lo em uma relação de confiança superior. O problema piora quando o chamador pode influenciar a geração de código, portanto certifique-se de que somente o código que você considerar seguros é gerado.  
  
 Você precisa saber exatamente o que o código que você está gerando em todos os momentos. Isso significa que você deve ter a controles rígidos em quaisquer valores que você obteve de um usuário, sejam eles delimitada por aspas cadeias de caracteres (que devem ser de escape para que elas não podem incluir elementos de código inesperado), identificadores (que devem ser verificados para verificar se eles são válidos identificadores), ou qualquer outra coisa. Identificadores podem ser perigosos, pois um assembly compilado pode ser modificado para que seus identificadores contêm caracteres estranhos, que serão interrompido ele provavelmente (embora isso raramente é uma vulnerabilidade de segurança).  
  
 É recomendável que você gerar o código com reflexão emissão, que geralmente ajuda a evitar muitos desses problemas.  
  
 Quando você compila o código, considere se há alguma forma de que um programa mal-intencionado pode modificá-lo. Há um pequeno intervalo de tempo durante o qual um código mal-intencionado pode alterar código-fonte no disco antes do compilador lê-lo ou antes de seu código carrega o arquivo. dll? Nesse caso, você deve proteger o diretório que contém esses arquivos, usando uma lista de controle de acesso no sistema de arquivos, conforme apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)

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
ms.openlocfilehash: ffb1081c80c31353ad38080ae16ef9f8a74b5481
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638013"
---
# <a name="security-and-on-the-fly-code-generation"></a>Segurança e geração de código durante a execução
Algumas bibliotecas operam por geração de código e executá-lo para executar alguma operação para o chamador. O problema básico é a geração de código em nome do código de confiança menor e executá-lo em uma relação de confiança mais alto. O problema piora quando o chamador pode influenciar a geração de código, portanto, você deve garantir que somente o código que você considerar seguros é gerado.  
  
 Você precisa saber exatamente o código que você está gerando em todos os momentos. Isso significa que você deve ter controles estritos em quaisquer valores que você obteve de um usuário, sejam colocados de cotação de cadeias de caracteres (que devem ser substituídas para que elas não podem incluir elementos de código inesperado), identificadores (que devem ser verificados para verificar se eles são válidos identificadores), ou qualquer outra coisa. Identificadores podem ser perigosos porque um assembly compilado pode ser modificado para que seus identificadores contêm caracteres estranhos, o que provavelmente interromperá a ele (embora isso raramente é uma vulnerabilidade de segurança).  
  
 É recomendável que você gerar código com a reflexão emite, que geralmente ajuda a evitar muitos desses problemas.  
  
 Quando você compila o código, considere se há alguma forma de que um programa mal-intencionado pode modificá-lo. Há uma pequena janela de tempo durante o qual código mal-intencionado pode alterar o código-fonte no disco antes do compilador lê-lo ou antes de seu código carrega o arquivo. dll? Nesse caso, você deve proteger o diretório que contém esses arquivos, usando uma lista de controle de acesso no sistema de arquivos, conforme apropriado.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)

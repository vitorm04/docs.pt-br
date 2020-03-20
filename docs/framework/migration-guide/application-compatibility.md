---
title: Tempo de execução e redirecionamento de alterações - .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196702"
---
# <a name="application-compatibility-in-the-net-framework"></a>Compatibilidade de aplicativos no Framework .NET

A compatibilidade é um objetivo importante de cada versão .NET. A compatibilidade garante que cada versão seja aditiva, de modo que as versões anteriores continuarão a funcionar. Por outro lado, alterações na funcionalidade anterior (por exemplo, para melhorar o desempenho, resolver problemas de segurança ou corrigir bugs) podem causar problemas de compatibilidade no código existente ou aplicativos existentes que são executados em uma versão posterior.

Cada aplicativo tem como alvo uma versão específica do .NET Framework por:

- Definição de uma estrutura de destino no Visual Studio.
- Especificação da estrutura de destino em um arquivo de projeto.
- Aplicação de um <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ao código-fonte.

Ao migrar de uma versão do .NET Framework para outra, existem dois tipos de alterações a considerar:

- [Alterações de tempo de execução](#runtime-changes)
- [Redirecionamento de alterações](#retargeting-changes)

## <a name="runtime-changes"></a>Alterações em runtime

Problemas de tempo de execução são aqueles que surgem quando um novo tempo de execução é colocado em uma máquina e o comportamento de um aplicativo muda. Ao ser executado em uma versão mais recente do que o que foi visado, o .NET Framework usa comportamento *peculiar* para imitar a versão direcionada mais antiga. O aplicativo é executado na versão mais recente, mas age como se estivesse sendo executado na versão mais antiga. Muitos dos problemas de compatibilidade entre versões do .NET Framework são atenuados com esse modelo de peculiaridade. Por exemplo, se um binário foi compilado para o .NET Framework 4.0, mas é executado em uma máquina com o .NET Framework 4.5 ou posterior, ele será executado no modo de compatibilidade .NET Framework 4.0. Isso significa que muitas das alterações na versão posterior não afetam o binário.

A versão do .NET Framework que um aplicativo segmenta é determinada pela versão de destino do conjunto de entrada para o domínio do aplicativo em que o código é executado. Todos os conjuntos adicionais carregados nesse destino de domínio visam essa versão. Por exemplo, no caso de um executável, a versão que os alvos executáveis são o modo de compatibilidade que todos os conjuntos nesse domínio de aplicativo são executados.

Para ver uma lista de alterações de tempo de execução que se aplicam ao seu ambiente, selecione a versão .NET Framework que você está mirando no momento e, em seguida, a versão para a qual deseja migrar:

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Alterações de redirecionamento

As alterações de redirecionamento são aquelas que surgem quando um conjunto é recompilado para atingir uma versão mais recente. Direcionar uma versão mais recente significa que o conjunto opta pelos novos recursos, bem como possíveis problemas de compatibilidade para recursos antigos.

Para ver uma lista de alterações de redirecionamento que se aplicam ao seu ambiente, selecione a versão .NET Framework que você está mirando no momento e, em seguida, a versão para a qual deseja migrar:

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Classificação de impacto

Nos tópicos que descrevem as alterações de tempo de execução e redirecionamento, por exemplo, [redirecionando alterações para migrar de 4.7.2 para 4.8](retargeting/4.7.2-4.8.md), os itens individuais são classificados pelo impacto esperado da seguinte forma:

**Principais**\
Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código.

**Menor**\
Uma alteração que afeta um pequeno número de aplicativos ou que exige modificação secundária do código.

**Caixa de borda**\
Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.

**Transparente**\
Uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.

## <a name="see-also"></a>Confira também

- [Versões e dependências](versions-and-dependencies.md)
- [Novidades](../whats-new/index.md)
- [O que é obsoleto](../whats-new/whats-obsolete.md)

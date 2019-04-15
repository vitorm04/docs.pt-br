---
title: Compatibilidade de aplicativos no .NET Framework
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcbcced47cfb2031e4a35a7437ec875a20354eed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176248"
---
# <a name="application-compatibility-in-the-net-framework"></a>Compatibilidade de aplicativos no .NET Framework

## <a name="introduction"></a>Introdução
A compatibilidade é uma meta muito importante de cada versão do .NET. A compatibilidade garante que cada versão é aditiva e, portanto, as versões anteriores ainda funcionarão. Por outro lado, as alterações na funcionalidade anterior (para melhorar o desempenho, resolver problemas de segurança ou corrigir bugs) podem causar problemas de compatibilidade no código ou nos aplicativos existentes que são executados em uma versão posterior. O .NET Framework reconhece as alterações de redirecionamento e de tempo de execução. As alterações de redirecionamento afetam os aplicativos que se destinam a uma versão específica do .NET Framework, mas que são executados em uma versão posterior. As alterações de tempo de execução afetam todos os aplicativos executados em uma versão específica.

Cada aplicativo se destina a uma versão específica do .NET Framework, que pode ser especificada por meio da:

* Definição de uma estrutura de destino no Visual Studio.
* Especificação da estrutura de destino em um arquivo de projeto.
* Aplicação de um <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ao código-fonte.

Quando for executado em uma versão mais recente do que a versão à qual foi destinado, o .NET Framework usará o comportamento peculiar para simular a versão de destino mais antiga. Em outras palavras, o aplicativo será executado na versão mais recente do Framework, mas atuará como se estivesse sendo executado na versão mais antiga. Muitos dos problemas de compatibilidade entre versões do .NET Framework são atenuados com esse modelo de peculiaridade. A versão do .NET Framework para a qual um aplicativo é direcionado é determinada pela versão de destino do assembly de entrada para o domínio do aplicativo no qual o código está em execução. Todos os assemblies adicionais carregados nesse domínio do aplicativo são direcionados a essa versão do .NET Framework. Por exemplo, no caso de um executável, a estrutura à qual o executável é direcionado é o modo de compatibilidade no qual todos os assemblies desse AppDomain serão executados.

## <a name="runtime-changes"></a>Alterações em tempo de execução

Problemas de tempo de execução são aqueles que surgem quando um novo tempo de execução é colocado em um computador e os mesmos binários são executados, mas um comportamento diferente é observado. Se um binário foi compilado para o .NET Framework 4.0, ele será executado no modo de compatibilidade do .NET Framework 4.0 na versão 4.5 ou em versões posteriores. Muitas das alterações que afetam a versão 4.5 não afetarão um binário compilado para a versão 4.0. Isso é específico a um AppDomain e depende das configurações do assembly de entrada.

## <a name="retargeting-changes"></a>Alterações de redirecionamento

Problemas de redirecionamento são aqueles que surgem quando um assembly que era destinado à versão 4.0 agora está definido para ter a versão 4.5 como destino. Agora o assembly aceita os novos recursos, bem como os possíveis problemas de compatibilidade dos recursos antigos. Novamente, isso é determinado pelo assembly de entrada e, portanto, o aplicativo de console que usa o assembly ou o site que referencia o assembly.

## <a name="net-compatibility-diagnostics"></a>Diagnóstico de Compatibilidade do .NET

O Diagnóstico de Compatibilidade do .NET são analisadores capacitados pelo Roslyn que ajudam a identificar problemas de compatibilidade de aplicativos entre versões do .NET Framework. Esta lista contém todos os analisadores disponíveis, embora apenas um subconjunto seja aplicado a qualquer migração específica. Os analisadores determinarão quais problemas se aplicam à migração planejada e os trará à tona.

Cada problema inclui as seguintes informações:

-   A descrição do que mudou em relação a uma versão anterior.

-   Como a alteração afeta os clientes e se alguma solução alternativa está disponível para preservar a compatibilidade entre versões.

-   Uma avaliação da importância da alteração. O problema de compatibilidade de aplicativos é categorizado como se segue:

    |   |   |
    |---|---|
    |Principal|Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código.|
    |Secundário|Uma alteração que afeta um pequeno número de aplicativos ou que exige modificação secundária do código.|
    |Caso de borda|Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.|
    |Transparente|Uma alteração que não afeta visivelmente o desenvolvedor nem o usuário do aplicativo.|

-   A versão indica quando a alteração aparece pela primeira vez na estrutura. Algumas alterações são introduzidas em uma versão específica e revertidas em uma versão posterior; isso também é indicado.

-   O tipo de alteração:

    |   |   |
    |---|---|
    |Redirecionando|A alteração afeta aplicativos que são recompilados para uma nova versão do .NET Framework.|
    |Tempo de execução|A alteração afeta um aplicativo existente que se destina a uma versão anterior do .NET Framework, mas é executado em uma versão posterior.|

-   As APIs afetadas, se houver.

-   As IDs do diagnóstico disponível

## <a name="usage"></a>Uso
Para começar, selecione o tipo de alteração de compatibilidade abaixo:

* [Alterações de redirecionamento](./retargeting/index.md)
* [Alterações em tempo de execução](./runtime/index.md)

## <a name="see-also"></a>Consulte também

- [Versões e dependências](../../../docs/framework/migration-guide/versions-and-dependencies.md)
- [O Que Há de Novo](../../../docs/framework/whats-new/index.md)
- [O que está obsoleto na biblioteca de classes](../../../docs/framework/whats-new/whats-obsolete.md)

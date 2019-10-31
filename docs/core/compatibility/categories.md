---
title: Categorias de alteração da falha – .NET Core
description: Saiba mais sobre as maneiras como as alterações da falha são categorizadas no .NET Core.
ms.date: 06/10/2019
ms.openlocfilehash: 058f2c2cdeed1e3e984f1de8ab493971d3937876
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089439"
---
# <a name="breaking-change-categories"></a>Categorias de alteração significativa

A *compatibilidade* refere-se à capacidade de compilar ou executar código em uma versão de uma implementação do .NET que não seja aquela com a qual o código foi originalmente desenvolvido. Uma alteração específica pode afetar a compatibilidade de seis maneiras diferentes. Os [tipos individuais de alterações consideradas ao avaliar a compatibilidade](index.md) se enquadram nas cinco primeiras categorias. 

## <a name="behavioral-change"></a>Alteração de comportamento

Uma alteração de comportamento representa uma alteração no comportamento de um membro. A alteração pode estar externamente visível (por exemplo, um método pode gerar uma exceção diferente) ou pode representar uma implementação alterada (por exemplo, uma alteração na maneira como um valor retornado é calculado, a adição ou a remoção de chamadas de método internas ou até mesmo uma melhoria significativa no desempenho).

Quando alterações de comportamentais estão externamente visíveis e modificam o contrato público de um tipo, elas são fáceis de avaliar, pois afetam a compatibilidade binária. As alterações de implementação são muito mais difíceis de avaliar; dependendo da natureza da alteração e da frequência e dos padrões de uso da API, o impacto de uma alteração pode variar de severo a inofensivo.  

## <a name="binary-compatibility"></a>Compatibilidade binária

A compatibilidade binária refere-se à capacidade de um consumidor de uma API de usar a API em uma versão mais recente sem recompilação. Essas alterações como adicionar métodos ou uma nova implementação de interface a um tipo não afetam a compatibilidade binária. No entanto, remover ou alterar as assinaturas públicas de um assembly para os consumidores não poderem mais acessar a mesma interface exposta pelo assembly afeta a compatibilidade binária. Uma alteração desse tipo é conhecida como uma *alteração incompatível de binário*.

## <a name="source-compatibility"></a>Compatibilidade de origem

 A compatibilidade de origem refere-se à capacidade de os consumidores existentes de uma API recompilarem com relação a uma versão mais recente sem nenhuma alteração de origem. Uma *alteração incompatível de origem* ocorre quando um consumidor precisa modificar um código-fonte para que ele seja criado com êxito em uma versão mais recente de uma API.

## <a name="design-time-compatibility"></a>Compatibilidade de tempo de design

A compatibilidade de tempo de design refere-se à preservação da experiência de tempo de design entre versões do Visual Studio e outros ambientes de tempo de design. Embora isso possa envolver o comportamento ou a interface do usuário dos designers, o aspecto mais importante da compatibilidade de tempo de design diz respeito à compatibilidade do projeto. Um projeto ou solução deve poder ser aberto e usado em uma versão mais recente do ambiente de tempo de design.

## <a name="backwards-compatibility"></a>Compatibilidade com versões anteriores

A compatibilidade com versões anteriores refere-se à capacidade de um consumidor existente de executar em uma nova versão quando se comporta da mesma maneira. As alterações de comportamento e as alterações na compatibilidade binária afetam a compatibilidade com versões anteriores. Se um consumidor não puder executar ou se comportar de maneira diferente ao ser executado na versão mais recente da API, a API será *incompatível com versões anteriores*.

Alterações que afetam a compatibilidade com versões anteriores são altamente desencorajadas, pois os desenvolvedores esperam, por padrão, a compatibilidade com versões anteriores em versões mais recentes de uma API.

## <a name="forward-compatibility"></a>Compatibilidade com versões posteriores

A compatibilidade com versões posteriores refere-se à capacidade de um consumidor existente de uma API de executar em uma versão mais antiga ao exibir o mesmo comportamento. Se um consumidor não puder executar ou se comportar de maneira diferente ao executar em uma versão mais antiga da API, a API será *incompatível com versões posteriores*. 

Manter a compatibilidade com versões posteriores praticamente impede alterações ou adições de versão para versão, pois essas alterações impedem que um consumidor que direciona uma versão posterior execute em uma versão anterior. Os desenvolvedores esperam que um consumidor que depende de uma API mais recente talvez não funcione corretamente com a API mais antiga. 

Manter a compatibilidade com versões futuras não é uma meta do .NET Core.

## <a name="see-also"></a>Consulte também

- [Avaliar alterações da falha no .NET Core](index.md)

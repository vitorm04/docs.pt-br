---
title: Membros (F#)
description: 'Saiba mais sobre os membros de objeto em F # linguagem de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: 6dcdb1d7fa061fb838d4aa8f7a2912fd168c3781
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="members"></a>Membros

Esta seção descreve os membros dos tipos de objeto do F#.


## <a name="remarks"></a>Comentários
*Membros* são recursos que fazem parte de uma definição de tipo e são declarados com a palavra-chave `member`. Tipos de objeto F# como registros, classes, uniões discriminadas, interfaces e membros de suporte às estruturas. Para saber mais, veja [Registros](../records.md), [Classes](../classes.md), [Uniões discriminada](../discriminated-Unions.md), [Interfaces](../interfaces.md) e [estruturas](../structures.md).

Os membros normalmente compõem a interface pública de um tipo e, por isso, são públicos, a menos que o contrário seja especificado. Os membros também podem ser declarados particular ou internamente. Para saber mais, veja [Controle de acesso](../access-Control.md). As assinaturas para tipos também podem ser usadas para expor ou não certos membros de um tipo. Para saber mais, confira [Assinaturas](../signatures.md).

Campos particulares e associações `do`, usados apenas com classes, não são membros reais, pois não fazem parte da interface pública de um tipo e não são declarados com a palavra-chave `member`, mas estão descritos nesta seção também.


## <a name="related-topics"></a>Tópicos relacionados


|Tópico|Descrição|
|-----|-----------|
|[`let`Associações em Classes](let-bindings-in-classes.md)|Descreve a definição de campos particulares e funções em classes.|
|[`do`Associações em Classes](do-bindings-in-classes.md)|Descreve a especificação do código de inicialização de objeto.|
|[Propriedades](properties.md)|Descreve os membros da propriedade em classes e outros tipos.|
|[Propriedades Indexadas](indexed-properties.md)|Descreve propriedade do tipo matriz em classes e outros tipos.|
|[Métodos](methods.md)|Descreve as funções que são membros de um tipo.|
|[Construtores](constructors.md)|Descreve funções especiais que inicializam objetos de um tipo.|
|[Sobrecarga de Operador](../operator-overloading.md)|Descreve a definição dos operadores personalizados para os tipos.|
|[Eventos](events.md)|Descreve a definição de eventos e suporte de manipulação de eventos em F#.|
|[Campos Explícitos: a `val` Palavra-Chave](explicit-fields-the-val-keyword.md)|Descreve a definição dos campos não inicializados em um tipo.|

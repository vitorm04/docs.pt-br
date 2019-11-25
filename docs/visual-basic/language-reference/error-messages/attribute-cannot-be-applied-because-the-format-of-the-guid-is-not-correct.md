---
title: "'<attribute>' não pode ser aplicado porque o formato da GUID '<number>' não está correto"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: f7b6e42480075666ce9f7e8fc6966bd4bb6b888a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977311"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>Não é possível aplicar '\<attribute > ' porque o formato do GUID '\<número > ' não está correto

Um bloco de atributo `COMClassAttribute` especifica um GUID (identificador global exclusivo) que não está de acordo com o formato adequado para um GUID. o `COMClassAttribute` usa GUIDs para identificar exclusivamente a classe, a interface e o evento de criação.  
  
 Um GUID consiste em 16 bytes, dos quais os oito primeiros são numéricos e os oito últimos são binários. Ele é gerado por utilitários da Microsoft como o Uuidgen. exe e é garantido que seja exclusivo em espaço e tempo.  
  
 **ID do erro:** BC32500  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Determine o GUID ou GUIDs corretos necessários para identificar o objeto COM.  
  
2. Certifique-se de que as cadeias de caracteres GUID apresentadas para o bloco de atributo `COMClassAttribute` sejam copiadas corretamente.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Guid>
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)

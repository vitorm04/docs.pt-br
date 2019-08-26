---
title: Parâmetros de método – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 4011cbd3bc9306b64df87b1fcde48f1f41df8240
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602042"
---
# <a name="method-parameters-c-reference"></a>Parâmetros de método (Referência de C#)

Os parâmetros declarados para um método sem [in](./in-parameter-modifier.md), [ref](./ref.md) nem [out](./out-parameter-modifier.md) são passados para o método chamado pelo valor. Esse valor pode ser alterado no método, mas o valor alterado não será mantido quando o controle passá-lo de volta para o procedimento de chamada. É possível alterar esse comportamento usando uma palavra-chave de parâmetro de método.  
  
 Esta seção descreve as palavras-chave que podem ser usadas ao declarar parâmetros de método:  
  
- [params](./params.md) especifica que esse parâmetro pode receber um número variável de argumentos.
  
- [in](./in-parameter-modifier.md) especifica que esse parâmetro é passado por referência, mas é lido apenas pelo método chamado.
  
- [ref](./ref.md) especifica que esse parâmetro é passado por referência e pode ser lido ou gravado pelo método chamado.
  
- [out](./out-parameter-modifier.md) especifica que esse parâmetro é passado por referência e é gravado pelo método chamado.
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](./index.md)

---
title: Protegendo dados de estado
description: Declare os dados estatais como variáveis privadas ou internas para limitar o acesso a eles. Esses dados ainda podem ser acessados através de reflexão, serialização e depuração.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: f95bf409f7eef8c2636d3c180d2bbd95fbc689c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186818"
---
# <a name="securing-state-data"></a>Protegendo dados de estado
Aplicativos que lidam com dados confidenciais ou tomam qualquer tipo de decisão de segurança precisam manter esses dados seu próprio controle e não podem permitir que outro código potencialmente malicioso acesse os dados diretamente. A melhor maneira de proteger dados na memória é declarar os dados como variáveis privadas ou internas (com escopo limitado ao mesmo conjunto). No entanto, mesmo esses dados estão sujeitos ao acesso que você deve estar ciente:  
  
- Usando mecanismos de reflexão, um código altamente confiável que pode referenciar seu objeto pode obter e definir membros privados.  
  
- Usando serialização, o código altamente confiável pode efetivamente obter e definir membros privados se ele puder acessar os dados correspondentes na forma serializada do objeto.  
  
- depuração, esses dados podem ser lidos.  
  
 Certifique-se de que nenhum de seus próprios métodos ou propriedades exponha esses valores involuntariamente.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)

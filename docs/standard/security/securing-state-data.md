---
title: Protegendo dados de estado
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: c30bd2fe9e1ed371be2db60739d3b329fea788c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705893"
---
# <a name="securing-state-data"></a>Protegendo dados de estado
Os aplicativos que lidam com dados confidenciais ou que fazem qualquer tipo de decisões de segurança precisam manter esses dados sob seu próprio controle e não podem permitir que outros códigos potencialmente mal-intencionados acessem os dados diretamente. A melhor maneira de proteger os dados na memória é declarar os dados como privados ou internos (com escopo limitado às variáveis do mesmo assembly). No entanto, mesmo esses dados estão sujeitos ao acesso que você deve estar ciente:  
  
- Usando mecanismos de reflexão, um código altamente confiável que pode fazer referência a seu objeto pode obter e definir membros privados.  
  
- Usar o código de serialização e altamente confiável pode efetivamente obter e definir membros privados se puder acessar os dados correspondentes na forma serializada do objeto.  
  
- Em depuração, esses dados podem ser lidos.  
  
 Certifique-se de que nenhum de seus próprios métodos ou Propriedades exponha esses valores involuntariamente.  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)

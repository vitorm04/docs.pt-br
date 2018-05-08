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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe941fff7091fb579e41a3c417dbb2129bcf3e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="securing-state-data"></a>Protegendo dados de estado
Aplicativos que lidam com dados confidenciais ou fazer qualquer tipo de decisões de segurança necessário manter esses dados em seu próprio controle e não podem permitir que outros códigos possivelmente mal-intencionados acessem os dados diretamente. É a melhor maneira de proteger os dados na memória para declarar os dados como privadas ou internas (com escopo limitado ao mesmo assembly) variáveis. No entanto, até mesmo esses dados são sujeitas a acesso que deve estar atento:  
  
-   Usando mecanismos de reflexão, código altamente confiável que pode fazer referência o objeto pode obter e definir membros particulares.  
  
-   Uso de serialização, código altamente confiável pode efetivamente obter e definir membros particulares se ele pode acessar os dados correspondentes no formato serializado do objeto.  
  
-   Na depuração, esses dados podem ser lidos.  
  
 Verifique se que nenhum dos seus próprios métodos ou propriedades expõe esses valores acidentalmente.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)

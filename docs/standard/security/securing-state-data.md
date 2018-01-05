---
title: Protegendo dados de estado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d5f8c4d17e17f7bcdf58db7052dbb2cf2b737a9c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="securing-state-data"></a>Protegendo dados de estado
Aplicativos que lidam com dados confidenciais ou fazer qualquer tipo de decisões de segurança necessário manter esses dados em seu próprio controle e não podem permitir que outros códigos possivelmente mal-intencionados acessem os dados diretamente. É a melhor maneira de proteger os dados na memória para declarar os dados como privadas ou internas (com escopo limitado ao mesmo assembly) variáveis. No entanto, até mesmo esses dados são sujeitas a acesso que deve estar atento:  
  
-   Usando mecanismos de reflexão, código altamente confiável que pode fazer referência o objeto pode obter e definir membros particulares.  
  
-   Uso de serialização, código altamente confiável pode efetivamente obter e definir membros particulares se ele pode acessar os dados correspondentes no formato serializado do objeto.  
  
-   Na depuração, esses dados podem ser lidos.  
  
 Verifique se que nenhum dos seus próprios métodos ou propriedades expõe esses valores acidentalmente.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)

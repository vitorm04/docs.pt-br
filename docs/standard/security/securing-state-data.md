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
ms.openlocfilehash: 85a12fb52efe32083d21b9aad50f2d9c1d6f0785
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602497"
---
# <a name="securing-state-data"></a>Protegendo dados de estado
Aplicativos que lidam com dados confidenciais ou fazer qualquer tipo de decisões de segurança necessário manter esses dados em seu próprio controle e não é possível permitir que outro código potencialmente mal-intencionado acessar os dados diretamente. A melhor maneira de proteger os dados na memória é declarar os dados como privado ou interno (com escopo limitado ao mesmo assembly) variáveis. No entanto, até mesmo com esses dados são sujeito ao acesso, que você deve estar atento:  
  
- Usando mecanismos de reflexão, código altamente confiável que pode fazer referência a seu objeto pode obter e definir os membros privados.  
  
- Usando a serialização, código altamente confiável pode efetivamente obter e definir os membros privados se ele pode acessar os dados correspondentes no formato serializado do objeto.  
  
- Na depuração, esses dados podem ser lidos.  
  
 Verifique se nenhum dos seus próprios métodos ou propriedades expõe esses valores acidentalmente.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)

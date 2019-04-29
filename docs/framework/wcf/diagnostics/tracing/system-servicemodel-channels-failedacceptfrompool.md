---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: de0bdd9e5ab922b09249bf550fde745042be8e58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666749"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a>System.ServiceModel.Channels.FailedAcceptFromPool
Falha ao tentar reutilizar uma conexão em pool. Outra tentativa é feita dentro do período de tempo limite especificado.  
  
## <a name="description"></a>Descrição  
 Este rastreamento informativo indica que ocorreu um erro durante a tentativa de reutilizar uma conexão em pool. Isso pode acontecer porque a conexão em pool não era compatível, pronto ou ainda está ativa. Tentativas adicionais de reutilizar outra conexão em pool são feitas dentro do tempo limite determinado e uma conexão nova é criada, caso nenhuma conexão utilizável é encontrado.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)

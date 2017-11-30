---
title: 'Sobre o CustomPeerResolverService: Registro de clientes'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b157d177b238db655e98a4cbe1d5a86ae895afa1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>Sobre o CustomPeerResolverService: Registro de clientes
Cada nó na malha publica suas informações de ponto de extremidade para o serviço de resolução por meio de `Register` função. O serviço resolvedor armazena essas informações como um registro. Este registro contém um identificador exclusivo (RegistrationID) e informações de ponto de extremidade (PeerNodeAddress) para o nó.  
  
## <a name="stale-records-and-expiration-time"></a>Registros obsoletos e a hora de expiração  
 Idealmente, quando um nó sai da malha, ele chamará o `Unregister` função, o que faz com que o serviço de resolução remover a entrada de registro. Às vezes, nós desligado ou se tornar inacessíveis antes de chamar `Unregister`, deixando atrás de um registro obsoletos.  
  
 Registros obsoletos no serviço resolvedor podem causar falhas de conexão. Se um nó tentando se conectar a uma malha recebe informações de conexão obsoleto do serviço resolvedor, pode levar mais tempo para unir com êxito a malha. Registros obsoletos também ocupam memória. Sem um eficiente limpar o processo, o cache usado para armazenar os registros pode eventualmente estouro e o serviço de resolução de falhas.  
  
 O <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> marca cada registro com um tempo de expiração (DateTime) e armazena essas informações como parte do registro. O serviço usa a hora de expiração para identificar registros obsoletos. Implementações personalizadas devem fazer algo semelhante.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>Intervalo de atualização e para CleanupInterval  
 O `RefreshInterval` propriedade o <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> define por quanto tempo os registros estarão válidos na tabela de pesquisa de registro do serviço. Quando a quantidade de tempo fornecido para essa propriedade tiver passado para um determinado registro, que o registro se torna obsoleto e está marcado para exclusão.  
  
 O `CleanupInterval` propriedade o <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> informa quantas vezes o serviço para pesquisar e excluir registros obsoletos. O `CleanupInterval` deve ser definido como um tempo maior que ou igual ao `RefreshInterval` definido no serviço.  
  
 Para implementar seu próprio serviço de resolução, você precisa escrever uma função de manutenção para remover registros obsoletos. Há várias maneiras de fazer isso:  
  
-   **Manutenção periódica**: definir um timer para off periodicamente e percorrer o repositório de dados para excluir registros antigos. O <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> usa essa abordagem.  
  
-   **Exclusão passivo**: em vez de pesquisar ativamente registros obsoletos em intervalos regulares, você pode identificar e excluir registros obsoletos quando seu serviço já está executando outra função. Isso pode potencialmente lenta tempo de resposta para solicitações de clientes resolvedor, mas elimina a necessidade de um temporizador e pode ser mais eficiente se alguns nós são esperado para sair sem chamar `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime e atualização  
 Quando um nó se registra com um serviço de resolução, ele recebe um <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> objeto do serviço. Esse objeto tem um `RegistrationLifetime` propriedade que indica para o nó de quanto tempo ele tem antes do registro expira e é removido, o serviço de resolução. Se, por exemplo, o `RegistrationLifetime` é 2 minutos, o nó precisa chamar `Refresh` em menos de 2 minutos para garantir o registro permanecerá atualizado e não será excluído. Quando o serviço resolvedor recebe um `Refresh` solicitação, ele procura o registro e redefine a hora de expiração. Atualize o retorna um <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> do objeto com um `RegistrationLifetime` propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Resolvedor Peer](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)

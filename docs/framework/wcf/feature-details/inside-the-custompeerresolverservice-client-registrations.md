---
title: 'O custompeerresolverservice: Registros de cliente'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 90d40eb11dbfebf4a19ba4c42e0fd4b45a2b1e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541775"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>O custompeerresolverservice: Registros de cliente
Cada nó na malha publica suas informações de ponto de extremidade para o serviço de resolvedor por meio de `Register` função. O serviço de resolvedor armazena essas informações como uma gravação de registro. Esse registro contém um identificador exclusivo (RegistrationID) e informações de ponto de extremidade (PeerNodeAddress) para o nó.  
  
## <a name="stale-records-and-expiration-time"></a>Registros obsoletos e a hora de expiração  
 O ideal é que, quando um nó deixa a malha, ele chamará o `Unregister` função, que faz com que o serviço de resolvedor remover a entrada de registro. Às vezes, nós desligado ou se torne inacessíveis antes de chamar `Unregister`, deixando por trás de um registro obsoleto.  
  
 Registros obsoletos em seu serviço de resolvedor podem causar falhas de conexão. Se um nó tentando se conectar a uma malha recebe informações de conexão obsoleto do serviço de resolvedor, pode levar mais tempo para associar com êxito a malha. Registros obsoletos também ocupam memória. Sem um eficiente processo de limpeza, o cache usado para armazenar os registros, eventualmente, poderia overflow e o serviço de resolvedor de falhas.  
  
 O <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> marca cada registro com um tempo de expiração (DateTime) e armazena essas informações como parte do registro. O serviço usa o tempo de expiração para identificar registros obsoletos. As implementações personalizadas devem fazer algo semelhante.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval e CleanupInterval  
 O `RefreshInterval` propriedade do <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> define quanto tempo os registros de registro permanecerão válidos na tabela de pesquisa de registro do serviço. Quando a quantidade de tempo fornecido para essa propriedade tiver passado para um determinado registro, que o registro se torna obsoleto e será marcado para exclusão.  
  
 O `CleanupInterval` propriedade do <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> informa a frequência com que o serviço para procurar e excluir registros obsoletos do registro. O `CleanupInterval` deve ser definido como um tempo maior que ou igual ao `RefreshInterval` definido no serviço.  
  
 Para implementar seu próprio serviço de resolvedor, você precisa escrever uma função de manutenção para remover registros obsoletos do registro. Há várias maneiras de fazer isso:  
  
-   **Manutenção periódica**: Defina um timer desativar periodicamente, e percorrer o armazenamento de dados para excluir registros antigos. O <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> usa essa abordagem.  
  
-   **Exclusão de passivo**: Em vez de pesquisar ativamente registros obsoletos em intervalos regulares, você pode identificar e excluir registros obsoletos, quando o serviço já está executando a outra função. Isso pode potencialmente atrasar tempo de resposta às solicitações dos clientes resolvedor, mas ele elimina a necessidade de um temporizador e pode ser mais eficiente se alguns nós são esperado para sair sem chamar `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime e atualização  
 Quando um nó é registrado com um serviço de resolvedor, ele recebe um <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> objeto do serviço. Esse objeto tem um `RegistrationLifetime` propriedade que indica para o nó de quanto tempo ela tem antes do registro expire e seja removido pelo serviço resolvedor. Se, por exemplo, o `RegistrationLifetime` é 2 minutos, o nó precisa chamar `Refresh` em menos de 2 minutos para garantir o registro permaneça atualizado e não é excluído. Quando o serviço de resolvedor recebe um `Refresh` solicitação, ele procura o registro e redefine a hora de expiração. Atualizar retorna um <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> do objeto com um `RegistrationLifetime` propriedade.  
  
## <a name="see-also"></a>Consulte também
- [Resolvedores pares](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)

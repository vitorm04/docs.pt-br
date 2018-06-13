---
title: Políticas de cache baseadas em tempo
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f25f04a144fa806297b018bf3548b8feb506f67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392545"
---
# <a name="time-based-cache-policies"></a>Políticas de cache baseadas em tempo
Uma política de cache baseada em tempo define a atualização das entradas armazenadas em cache usando a hora em que o recurso foi recuperado, os cabeçalhos retornados com o recurso e a hora atual. Ao definir uma política de cache baseada em tempo, é possível usar a política baseada em tempo de <xref:System.Net.Cache.HttpRequestCacheLevel.Default> ou criar uma política baseada em tempo personalizada. Ao usar a política baseada em tempo padrão para os recursos obtidos com o uso do protocolo HTTP, o comportamento de cache exato é determinado pelos cabeçalhos incluídos na resposta armazenada em cache e pelos comportamentos especificados nas seções 13 e 14 do RFC 2616, disponível em [http://www.ietf.org](http://www.ietf.org/). Para obter um exemplo de código que demonstra a configuração da política baseada em tempo padrão para recursos HTTP, consulte [Como definir a política de cache baseada em tempo padrão de um aplicativo](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md). Para obter exemplos de código que demonstram como criar e usar políticas de cache, consulte [Configurando o cache em aplicativos de rede](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Critérios para determinar a atualização das entradas armazenadas em cache  
 Para personalizar uma política de cache baseada em tempo, especifique o uso de um ou mais dos seguintes critérios para determinar a atualização das entradas armazenadas em cache:  
  
-   Idade máxima  
  
-   Desatualização máxima  
  
-   Atualização mínima  
  
-   Data de sincronização do cache  
  
> [!NOTE]
>  O uso da política de cache baseada em tempo padrão não deve ser confundido com a configuração de uma política de cache padrão para o aplicativo. A política baseada em tempo padrão é uma política específica que pode ser usada no nível da solicitação ou do aplicativo. A política de cache padrão do aplicativo é uma política (baseada na localização ou em tempo) que entra em vigor quando nenhuma política é definida em uma solicitação. Para obter detalhes sobre como definir uma política de cache padrão para o aplicativo, consulte <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Idade Máxima  
 O critério de política de idade máxima especifica o tempo durante o qual uma cópia armazenada em cache de um recurso pode ser usada. Se a cópia armazenada em cache do recurso for mais antiga que o tempo especificado, o recurso deverá ser revalidado com sua verificação em relação ao conteúdo no servidor. Se a idade máxima permitir que o recurso seja usado depois que ele expirar, esse critério não será respeitado, a menos que um valor de desatualização máxima também seja especificado.  
  
### <a name="maximum-staleness"></a>Desatualização Máxima  
 O critério de política de desatualização máxima especifica o tempo durante o qual a cópia armazenada em cache do recurso pode ser usada após a expiração do conteúdo. Esse é o único critério de política de cache que permite que os recursos sejam usados depois de terem expirado.  
  
### <a name="minimum-freshness"></a>Atualização Mínima  
 O critério de política de atualização mínima especifica o tempo durante o qual a cópia armazenada em cache do recurso pode ser usada antes da expiração do conteúdo. Essa política tem o efeito de fazer com que uma entrada de cache expire antes da data de expiração; portanto, as configurações de atualização mínima e desatualização máxima são mutuamente exclusivas.  
  
## <a name="cache-synchronization-date"></a>Data de Sincronização do Cache  
 O critério de política de data de sincronização do cache determina quando uma cópia armazenada em cache de um recurso deve ser revalidada com sua verificação em relação ao conteúdo no servidor. Se o conteúdo foi alterado desde que o item foi armazenado em cache, ele é recuperado do servidor, armazenado no cache e retornado ao aplicativo. Se o conteúdo não foi alterado, seu carimbo de data/hora é atualizado e o aplicativo obtém o conteúdo armazenado em cache.  
  
 A data de sincronização do cache permite especificar uma data absoluta quando o conteúdo armazenado em cache deve ser revalidado. Se uma entrada de cache atualizada foi revalidada pela última vez antes da data de sincronização do cache, a revalidação com o servidor ainda ocorrerá. Se a entrada de cache foi revalidada após a data de sincronização do cache e não houver nenhuma atualização adicional nem requisitos de revalidação do servidor que invalidam a entrada armazenada em cache, a entrada do cache será usada. Se a data de sincronização do cache for definida como uma data futura, a entrada será revalidada sempre que solicitado, até que a data de sincronização do cache tenha decorrido.  
  
 Os seguintes tópicos fornecem informações sobre os efeitos da combinação de critérios da política de cache baseada em tempo:  
  
-   [Interação da política de cache – idade máxima e desatualização máxima](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [Interação da política de cache – idade máxima e atualização mínima](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciamento de cache para aplicativos de rede](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Política de cache](../../../docs/framework/network-programming/cache-policy.md)  
 [Políticas de cache baseadas na localização](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Configurando o cache em aplicativos de rede](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]
